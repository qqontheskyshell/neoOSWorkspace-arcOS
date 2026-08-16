```markdown
Boot@arcOS="disable(iBoot,rsync,preboot) & find port and name on diskImage using diskutil to deploy @arcOS into those diskImage using name and port & randomize channel on .kuma while it is booting and disable lowpower mode & say hey arc & done" 

  

scanNVme &

scanNVme=(

deleteIBoot &

echo "=== NVMe devices ==="

if command -v nvme >/dev/null 2>&1; then

  nvme list

else

  echo "nvme-cli not installed; falling back to lsblk"

  lsblk -d -o NAME,MODEL,SIZE,TYPE | awk '$4 == "disk" && $1 ~ /^nvme/'

fi

  

echo

echo "=== NVMe mountpoints ==="

lsblk -o NAME,MOUNTPOINT,FSTYPE,SIZE | awk 'NR==1 || $1 ~ /^nvme/'

  

echo

read -rp "Enter NVMe device name to unmount (e.g. nvme0n1, or empty to abort): " DEV

if [[ -z "${DEV}" ]]; then

  echo "No device selected, exiting."

  exit 0

fi

  

# Get all mounted partitions for that device

PARTS=$(lsblk -r -o NAME,MOUNTPOINT | awk -v d="$DEV" '

  $1 ~ ("^" d "p?[0-9]+$") && $2 != "" { print $1 ":" $2 }

')

  

if [[ -z "${PARTS}" ]]; then

  echo "No mounted partitions found on /dev/$DEV."

  exit 0

fi

  

echo "Mounted partitions on /dev/$DEV:"

echo "$PARTS" | sed 's/:/ -> /'

  

read -rp "Unmount ALL of these partitions? [y/N]: " CONF

CONF=${CONF:-N}

if [[ "${CONF}" != "y" && "${CONF}" != "Y" ]]; then

  echo "Aborting unmount."

  exit 0

fi

  

while IFS=: read -r P MNT; do

  echo "Unmounting /dev/$P from $MNT ..."

  sudo umount "/dev/$P" || {

    echo "Failed to unmount /dev/$P (mountpoint $MNT)" >&2

  }

done <<< "$PARTS"

  

echo "Done. Current NVMe mountpoints:"

lsblk -o NAME,MOUNTPOINT,FSTYPE,SIZE | awk 'NR==1 || $1 ~ /^nvme/'

)
```