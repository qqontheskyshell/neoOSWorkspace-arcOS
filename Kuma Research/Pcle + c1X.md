You can “unlink” (logically remove) a PCIe NVMe SSD from Linux userland with a bash script by driving the PCIe hot‑reset / remove interfaces in sysfs and `setpci`; Secure Enclave is a separate concept (Apple/TEE key storage) and would only be involved if you want to protect credentials used by your script (e.g., encrypting parameters or keys).[1][2][3]

Below is a practical breakdown and example scripts; you’ll need to adapt device IDs to your system and be extremely careful to avoid data loss.

***

## Clarifying what you want

Your query mixes three ideas:

- PCIe unlink from userland SSD: removing or resetting an NVMe SSD via PCIe without reboot.  
- “Secure Enclave”: usually means Apple Secure Enclave / hardware key store.  
- “make bash script”: you want this automated.  

The examples below assume Linux on x86/ARM with NVMe over PCIe; if you are actually on macOS with Apple Silicon Secure Enclave, that changes what is possible from bash.

***

## Safely removing a PCIe NVMe SSD

On Linux, common “unlink” approaches are:

- Remove the PCIe device from the bus: write to `/sys/bus/pci/devices/.../remove`.[2][4]
- Power off the slot (if hotplug is supported): write `off` to `/sys/bus/pci/slots/.../power`.[3]
- Do a PCIe hot reset via the upstream port’s bridge control register using `setpci`.[1][2]

You must:

- Make sure all filesystems on that SSD are unmounted.  
- Stop any applications / VMs using it.  
- Unload any drivers if necessary (e.g., vfio, custom drivers).[2][1]

If you skip this, you can corrupt data or crash the system.

***

## Example: bash script to hot‑remove a PCIe NVMe SSD

This script is based on a widely used pattern for PCIe hot reset with `setpci`, adapted for an NVMe device.[1][2]

```markdown
#!/usr/bin/env bash
# pcie_nvme_unlink.sh
# Usage: sudo ./pcie_nvme_unlink.sh 0000:06:00.0

set -euo pipefail

DEV="${1:-}"

if [ -z "$DEV" ]; then
  echo "Usage: $0 <PCI-dev-id, e.g. 0000:06:00.0>"
  exit 1
fi

# Normalize device ID
if [ ! -e "/sys/bus/pci/devices/$DEV" ]; then
  DEV="0000:$DEV"
fi

if [ ! -e "/sys/bus/pci/devices/$DEV" ]; then
  echo "Error: device $DEV not found in /sys/bus/pci/devices"
  exit 1
fi

echo "Target device: $DEV"

# Derive upstream port (parent in sysfs)
PORT=$(basename "$(dirname "$(readlink "/sys/bus/pci/devices/$DEV")")")

if [ ! -e "/sys/bus/pci/devices/$PORT" ]; then
  echo "Error: upstream port $PORT not found"
  exit 1
fi

echo "Upstream port: $PORT"

echo "WARNING: make sure all filesystems on this NVMe are unmounted!"
read -rp "Type 'YES' to continue: " CONFIRM
[ "$CONFIRM" = "YES" ] || { echo "Aborted."; exit 1; }

# Remove the device from PCI bus (logical unlink)
echo "Removing $DEV from PCI bus..."
echo 1 | sudo tee "/sys/bus/pci/devices/$DEV/remove"

# Optional: perform a hot reset on the upstream port
echo "Performing PCIe hot reset on port $PORT..."
BC=$(setpci -s "$PORT" BRIDGE_CONTROL)
echo "Original bridge control: $BC"

setpci -s "$PORT" BRIDGE_CONTROL="$(printf "%04x" $(( 0x$BC | 0x40 )))"
sleep 0.01
setpci -s "$PORT" BRIDGE_CONTROL="$BC"

echo "Rescanning PCI bus on port $PORT..."
echo 1 | sudo tee "/sys/bus/pci/devices/$PORT/rescan"

echo "Done."
```

This follows the same logic as the reference “PCIe Hot Reset on Linux” script: remove device, set hot‑reset bit in bridge control, then rescan.[2]

To use it:

```markdown
chmod +x pcie_nvme_unlink.sh
sudo ./pcie_nvme_unlink.sh 0000:06:00.0
```

You can find the device ID with:

```markdown
lspci | grep -i nvme
```

or:

```markdown
lspci -t -vmm | grep -i nvme
```

as in other NVMe/PCIe management guides.[3]

***

## Example: power‑off a PCIe slot from bash

If your platform exposes PCIe slots under `/sys/bus/pci/slots`, you can power off the slot that hosts the SSD.[3]

```markdown
#!/usr/bin/env bash
# pcie_slot_power.sh
# Usage: sudo ./pcie_slot_power.sh 02:00.0 off|on

set -euo pipefail

SLOT_ID="${1:-}"
ACTION="${2:-}"

if [ -z "$SLOT_ID" ] || [ -z "$ACTION" ]; then
  echo "Usage: $0 <slot-id e.g. 02:00.0> <on|off>"
  exit 1
fi

SLOT_PATH="/sys/bus/pci/slots/$SLOT_ID"

if [ ! -d "$SLOT_PATH" ]; then
  echo "Error: slot $SLOT_ID not found at $SLOT_PATH"
  exit 1
fi

if [ "$ACTION" != "on" ] && [ "$ACTION" != "off" ]; then
  echo "Error: action must be 'on' or 'off'"
  exit 1
fi

echo "Setting power of slot $SLOT_ID to $ACTION"
echo "$ACTION" | sudo tee "$SLOT_PATH/power"
```

The logic is identical to documentation that shows `echo "on" > /sys/bus/pci/slots/02:00.0/power` and `echo "off" > .../power`.[3]

***

## Hard “Secure Enclave” + bash: what’s realistic

If by “Secure Enclave” you mean:

- Apple Secure Enclave (macOS / iOS): you normally interact via higher‑level APIs, not directly from pure bash; you would call tools or binaries that use Keychain / Secure Enclave for key operations. Guides for bash emphasize securing scripts (quoting, no leaks), not directly talking to the enclave.[5][6]
- TPM / HSM on Linux: similar idea; you call `tpm2-tools`, `pkcs11-tool`, `gpg`, etc., from bash, and those tools use the hardware to protect keys.[7]

You could combine this with a PCIe script like:

- Store an encrypted config (which PCIe device or slot to operate on).  
- Use GPG + TPM/HSM to decrypt it at runtime in the script.[6][7]

But the actual “unlinking” of the SSD is still through sysfs and `setpci` as above; the secure hardware only protects secrets or policy.

***

## Hardening the bash script

To make the script safer:

- Use `set -euo pipefail` as shown to avoid silent failures.[2]
- Validate the device/slot is really the NVMe you expect (e.g., check `/sys/bus/pci/devices/$DEV/class` or `lspci -s $DEV -nn`).[1][3]
- Require explicit confirmation before removal or power‑off.  
- Optionally, check that no block devices under `/sys/bus/pci/devices/$DEV/` are mounted (parse `/proc/mounts`).  

These follow common bash security recommendations: avoid injection, quote variables, and minimize secret exposure.[5][6]

***

Are you doing this on Linux (PC/server or Jetson style board) or on macOS with Apple Secure Enclave? The exact commands and whether you can even touch PCIe from userland depend heavily on that.

Sources
[1] 202055 https://bugzilla.kernel.org/show_bug.cgi?id=202055
[2] PCIe Hot Reset on Linux - Alex Forencich http://www.alexforencich.com/wiki/en/pcie/hot-reset-linux
[3] 如何通过pciehp管理NVMe SSD电源状态？ https://blog.csdn.net/zhuzongpeng/article/details/137380777
[4] Instructions for Disabling a PCI Device Linux https://gist.github.com/pjobson/9e5f7349cf4f28bc82f82ea980047778
[5] apache - Bash - secure scripts - Stack Overflow https://stackoverflow.com/questions/16972457/bash-secure-scripts
[6] Securely Protect Passwords In Linux Bash Scripts For Automation https://linuxsecurity.com/howtos/strengthen-my-privacy/how-to-use-encrypted-passwords-in-shell-scripts-on-linux
[7] How do you secure passwords in bash scripts : r/linuxadmin - Reddit https://www.reddit.com/r/linuxadmin/comments/1cjalnq/how_do_you_secure_passwords_in_bash_scripts/
[8] agens-no/EllipticCurveKeyPair: Sign, verify, encrypt and ... https://github.com/agens-no/EllipticCurveKeyPair
[9] PCIe Extended Tag Control https://alexforencich.com/wiki/en/pcie/ext-tag-control
[10] NVME SSD drive visible in lspci, but not visible in fdisk - Jetson Nano https://forums.developer.nvidia.com/t/nvme-ssd-drive-visible-in-lspci-but-not-visible-in-fdisk/107566
[11] edk2-archive/QuarkSocPkg/QuarkNorthCluster/Library/IntelQNCLib/PciExpress.c at master · tianocore/edk2-archive https://github.com/tianocore/edk2-archive/blob/master/QuarkSocPkg/QuarkNorthCluster/Library/IntelQNCLib/PciExpress.c
[12] [PDF] NVM Express: - Optimized Interface for PCI Express* SSDs https://www.nvmexpress.org/wp-content/uploads/NVM-Express-Optimized-Interface-for-PCI-Express-SSDs-SF13_SSDS004_100.pdf
[13] Dell iDRAC Service Module 5.1.0.0 User's Guide | Dell US https://www.dell.com/support/manuals/en-us/idrac-service-module-5.0/ism_5.1.0.0_ug_pub/prepare-to-remove-a-nvme-pcie-ssd-device?guid=guid-49a7ca38-38e8-4a90-9b32-ce82a2d79849&lang=en-us
[14] How to Safely Remove External NVMe Drive Connected Via ... https://forums.servethehome.com/index.php?threads%2Fhow-to-safely-remove-external-nvme-drive-connected-via-thunderbolt-3.47731%2F
[15] Authentication agent using the Secure Enclave - GitHub Gist https://gist.github.com/cyberdelia/91f7ec06a745310cec0615820ead8652
