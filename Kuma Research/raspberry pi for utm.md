Here's a complete **bash script** to convert a Raspberry Pi `.img.xz` image so it can potentially work in UTM (though note: **Raspberry Pi emulation is still broken in UTM** per GitHub issue #4827). The script extracts the kernel/DTB files and converts to a format UTM can use:

## Bash Conversion Script

```markdown
#!/bin/bash

# Raspberry Pi .img.xz to UTM-compatible format converter
# Note: Raspberry Pi emulation is BROKEN in UTM (GitHub #4827)
# Use Debian ARM64 instead for reliable results

set -e

# Configuration
IMAGE_XZ="2024-05-24-raspios-arm64.img.xz"  # Your .img.xz file
OUTPUT_NAME="raspios-arm64"

echo "=== Raspberry Pi Image Converter for UTM/QEMU ==="

# Step 1: Extract .xz to .img
echo "Step 1: Extracting .xz file..."
unxz -f "$IMAGE_XZ" || xz -d "$IMAGE_XZ"
IMAGE_FILE="${IMAGE_XZ%.xz}"
echo "Extracted: $IMAGE_FILE"

# Step 2: Resize image to power of 2 (QEMU requirement)
echo "Step 2: Resizing image to 2GB..."
qemu-img resize -f raw "$IMAGE_FILE" 2G

# Step 3: Convert to qcow2 format (UTM-compatible)
echo "Step 3: Converting to qcow2 format..."
qemu-img convert -f raw -O qcow2 "$IMAGE_FILE" "${OUTPUT_NAME}.qcow2"

# Step 4: Mount and extract kernel + DTB files (required for QEMU/UTM)
echo "Step 4: Extracting kernel and device tree files..."

# Create mount directories
mkdir -p ./boot ./rootfs

# Mount image with partition table scanning
sudo losetup -f --show "$IMAGE_FILE" | while read LOOPDEV; do
    sudo mount "${LOOPDEV}p1" ./boot/
    sudo mount "${LOOPDEV}p2" ./rootfs/
    
    # Copy kernel and DTB files
    cp boot/kernel*.img ./
    cp boot/*-rpi-*.dtb ./
    
    sudo umount ./boot/
    sudo umount ./rootfs/
    sudo losetup -d "$LOOPDEV"
done

echo "Extracted files:"
ls -la kernel*.img *-rpi-*.dtb

# Step 5: Create UTM configuration file
echo "Step 5: Creating .utm configuration..."
cat > "${OUTPUT_NAME}.utm" << EOF
{
  "arch": "aarch64",
  "bootDevice": "sdcard",
  "cpu": "cortex-a72",
  "device": "raspi3b",
  "drives": [
    {
      "file": "${OUTPUT_NAME}.qcow2",
      "format": "qcow2",
      "interface": "sd"
    }
  ],
  "kernel": "kernel8.img",
  "dtb": "bcm2710-rpi-3-b.dtb",
  "memory": 1024,
  "append": "rw earlyprintk=loglevel=8 console=ttyAMA0,115200 root=/dev/mmcblk0p2 rootdelay=1"
}
EOF

echo ""
echo "=== Conversion Complete ==="
echo "Files created:"
echo "  - ${OUTPUT_NAME}.qcow2  (disk image for UTM)"
echo "  - ${OUTPUT_NAME}.utm    (UTM config file)"
echo "  - kernel8.img          (kernel for QEMU)"
echo "  - bcm2710-rpi-3-b.dtb  (device tree for QEMU)"
echo ""
echo "IMPORTANT: Raspberry Pi emulation is BROKEN in UTM!"
echo "Use Debian ARM64 instead: https://mac.getutm.app/gallery/"
```

## Quick One-Liner Commands

If you just want the minimal conversion:

```markdown
# Extract .xz
unxz your-image.img.xz

# Convert to qcow2
qemu-img convert -f raw -O qcow2 your-image.img raspios.qcow2

# Resize to 2GB (power of 2 required)
qemu-img resize raspios.qcow2 2G
```

## Alternative: Use Debian Instead (Recommended)

Since Raspberry Pi emulation is broken, just download **Debian ARM64** directly:

```markdown
# Download Debian ARM64 for Apple Silicon/iOS
wget https://downloads.debian.org/arm64/debian-arm64.img.xz

# Extract and convert
unxz debian-arm64.img.xz
qemu-img convert -f raw -O qcow2 debian-arm64.img debian-arm64.qcow2
```

This works reliably in UTM.[3][11]

Sources
[1] install .img files · utmapp UTM · Discussion #3391 - GitHub https://github.com/utmapp/UTM/discussions/3391
[2] Emulating ARM 64 RaspiOS - LinkedIn https://www.linkedin.com/pulse/emulating-arm-64-raspios-anthony-s-clark-68fec
[3] Gallery | UTM https://mac.getutm.app/gallery/
[4] Create Raspberry Pi 3B VM on QEMU - GitHub Gist https://gist.github.com/ruippeixotog/ef64833ca5d885bae3df3b9ceb5310ec
[5] How to download AND extract a .img.xz file? - Raspberry Pi Forums https://forums.raspberrypi.com/viewtopic.php?t=288076
[6] Unable to boot two latest arm64 releases of Raspberry Pi OS https://forums.raspberrypi.com/viewtopic.php?t=317299
[7] hello I was wondering, can I run raspberry pi os arm on UTM - Reddit https://www.reddit.com/r/UTMapp/comments/1oeonoc/hello_i_was_wondering_can_i_run_raspberry_pi_os/
[8] Raspberry Pi and QEMU | Marcus Folkesson Blog https://www.marcusfolkesson.se/blog/rpi-qemu/
[9] How to convert Raspberry Pi OS images and import to Proxmox https://forum.proxmox.com/threads/how-to-convert-raspberry-pi-os-images-and-import-to-proxmox.146837/
[10] Guides to emulate a Raspberry Pi OS (Buster / Bullseye) with QEMU https://www.reddit.com/r/qemu_kvm/comments/10my3rq/guides_to_emulate_a_raspberry_pi_os_buster/
[11] Raspberry Pi emulation is broken · Issue #4827 · utmapp/UTM https://github.com/utmapp/UTM/issues/4827
