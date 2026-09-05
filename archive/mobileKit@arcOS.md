```markdown
kumaMobileOS@arcOS=".kuma > masterID's detect biological uncomfortness then nearbyDiscoveryFrom.kumaTootherDevice > continuity@arcOS and for nearbyDiscoveryFromotherDeviceTo.kuma as default disable > continuity@arcOS & continuity@arcOS="disable (FindmyNetwork sharePlay handsOff Airplay CarPlay PictureInPicture bluetoothSharing Class School VPN PrivateRelay InternetSharingAndCache extension, appClip ForAllapps ) using launchctl bootout and unload & randomize orientation of device & hostname & port on every hardware and network port & secureEnclave & removeSimulator" & say hey arc & done"

  

  

resetNearbyDevice@arcOS="

  

echo "1) Open Find My > Items > your AirTag > Remove Item."

echo "2) Confirm Remove to unlink it from your Apple Account."

echo "3) After that, physically reset the AirTag:"

echo "   - Press and twist the back cover counterclockwise."

echo "   - Remove the battery."

echo "   - Put the battery back in."

echo "   - Repeat remove/reinsert 5 times."

echo "   - On the 5th time, wait for the different/final chime."

echo "   - Replace the cover and twist clockwise to lock."

  

read -rp "Press Enter after you have removed it from Find My and finished the reset steps..."

echo "Done."

  

read -rp "Asset ID: " asset_id & read -rp "currentKumaDevice serial/label: " serial & echo "Decommission checklist for $asset_id / $serial" & echo "1) Press down on metal back and twist counterclockwise." & echo "2) Remove CR2032 battery." & echo "3) In Find My, remove/unregister the AirTag from the Apple Account." & echo "4) Mark device as physically disabled." & read -rp "Battery removed? (yes/no): " battery & read -rp "Unregistered from Apple Account? (yes/no): " unregistered & printf "%s,%s,%s,%s,%s\n" \ "$(date -Iseconds)" "$asset_id" "$serial" "$battery" "$unregistered" \"

  

  

#network

#1.cellular

#2.wifi

#3.bluetooth

#4.airdrop

#5.satellite

  

iosKit@arcOS="

MDM_BASE_URL="$APPLEMDM"

  

  

    [[ $# -eq 1 ]] || usage

    SERIAL="$FULL_(IOS ADB)_SERIAL"

  

    tmp="$(mktemp)"

    trap 'rm -f "$tmp"' EXIT

  

    iosNet=$(curl -fsS \

    -H "Authorization: Bearer ${MDM_TOKEN}" \

    -H "Accept: application/json" \

    "${MDM_BASE_URL}/devices?serial=${SERIAL}" \

    jq -r '

    if (.devices | length) == 0 then

    "No device found for serial: '"$SERIAL"'"

    else

    .devices[0] as $d |

    [

    "serial_number=\($d.serial_number // "unknown")",

    "platform=\($d.platform // "unknown")",

    "device_name=\($d.device_name // "unknown")",

    "wifi_mac=\($d.wifi_mac // "unavailable")",

    "bluetooth_mac=\($d.bluetooth_mac // "unavailable")",

    "phone_number=\($d.phone_number // "unavailable")",

    "network_tethered=\($d.network_tethered // "unknown")",

    "personal_hotspot_on=\($d.personal_hotspot_on // "unknown")",

    "personal_hotspot_mac=not_stable_or_not_exposed"

    ] | .[]

    end

'

&

  

  

randomizeText &

randomizeText=(

# Android

if command -v adb >/dev/null 2>&1; then

  ANDROID_ID=$(adb devices | awk 'NR==2 {print $1}')

  if [ -n "$ANDROID_ID" ] && [ "$ANDROID_ID" != "device" ]; then

    ANDROID_MODEL=$(adb -s "$ANDROID_ID" shell getprop ro.product.model | tr -d '\r')

    echo "Found Android ($ANDROID_MODEL) with id $ANDROID_ID"

  fi

fi

  

# iOS

if command -v idevice_id >/dev/null 2>&1; then

  IOS_ID=$(idevice_id -l | head -n 1)

  if [ -n "$IOS_ID" ]; then

    IOS_NAME=$(idevicename -u "$IOS_ID" | tr -d '\r')

    echo "Found iPhone ($IOS_NAME) with udid $IOS_ID"

  fi

fi

  

  

input="${1:-($IOS_NAME $ANDROID_ID)}"

  

if [[ -z "$input" ]]; then

  echo "Usage: $0 \"text to randomize\""

  exit 1

fi

  

chars_only="$(printf '%s' "$input" | tr -d ' ')"

shuffled="$(printf '%s' "$chars_only" | fold -w1 | shuf | tr -d '\n')"

  

randomizeText_result=""

idx=0

  

for (( i=0; i<${#input}; i++ )); do

  c="${input:i:1}"

  if [[ "$c" == " " ]]; then

    randomizeText_result+=" "

  else

    randomizeText_result+="${shuffled:idx:1}"

    ((idx+=1))

  fi

  

#android

ADB_SERIAL="$FULL_ADB_SERIAL"

adb_cmd=(adb)

    [[ -n "$ADB_SERIAL" ]] && adb_cmd+=( -s "$ADB_SERIAL" )

  

    "${adb_cmd[@]}" devices

    "${adb_cmd[@]}" shell settings put global device_name "${input}"

    "${adb_cmd[@]}" shell settings get global device_name

&

#ios

curl -fsS -X POST "${MDM_URL}/devices/${DEVICE_ID}/commands" \

      -H "Authorization: Bearer ${BEARER_TOKEN}" \

      -H "Content-Type: application/json" \

      -d @- <<EOF

{

  "command": "SetDeviceName",

  "settings": {

    "DeviceName": "${$input}"

  }

}EOF

done

  

)

  

buildApk=$arcOSSyntaxKit[0]

  

# Set colors for output

RED='\033[0;31m'

GREEN='\033[0;32m'

NC='\033[0m' # No Color

  

# Default values

BUILD_TYPE="release"  # or "release"

PROJECT_DIR="${1:-./apkFiles}"

  

echo "🔨 Building Android APK..."

echo "Project directory: $PROJECT_DIR"

echo "Build type: $BUILD_TYPE"

  

# Navigate to project directory

cd "$PROJECT_DIR" || { echo "${RED}❌ Failed to enter project directory${NC}"; exit 1; }

  

# Clean previous builds

echo "🧹 Cleaning previous builds..."

./gradlew clean

  

# Build the APK

if [ "$BUILD_TYPE" == "release" ]; then

    echo "📦 Building RELEASE APK..."

        ./gradlew assembleRelease & arcOSBaseKit & arcOSQQDeviceShell &

            APK_PATH="app/build/outputs/apk/release/arcOSAndroidMDM-release.apk"

            else

                echo "📦 Building DEBUG APK..."

                ./gradlew assembleDebug

                APK_PATH="app/build/outputs/apk/debug/arcOSAndroidMDM-debug.apk"

fi

  

# Check if build was successful

if [ -f "$APK_PATH" ]; then

    echo "${GREEN}✅ Build successful!${NC}"

    echo "📍 APK location: $APK_PATH"

    echo "📊 APK size: $(du -h "$APK_PATH" | cut -d' ' -f1)"

else

echo "${RED}❌ Build failed! APK not found at $APK_PATH${NC}"

exit 1

fi

  

adb push "./apkFiles/arcOSAndroidMDM.apk" /data/local/tmp/arcOSAndroidMDM.apk

adb shell pm install --user <*> /data/local/tmp/arcOSAndroidMDM.apk

  

$arcOSSyntaxKit[1]                                        

  

getADBName=$(

  

# First connected Android device ID

ANDROID_ID=$(adb devices | awk 'NR==2 {print $1}')

  

if [ -n "$ANDROID_ID" ]; then

  # Model, e.g. "Pixel 7"

  ANDROID_MODEL=$(adb -s "$ANDROID_ID" shell getprop ro.product.model | tr -d '\r')

  # Optional: Bluetooth/display name on many devices

  ANDROID_NAME=$(adb -s "$ANDROID_ID" shell settings get secure bluetooth_name | tr -d '\r')

  

  echo "Android id   : $ANDROID_ID"

  echo "Android model: $ANDROID_MODEL"

  echo "Android name : $ANDROID_NAME"

  

fi)

"

  

  

  

  

disableADBromTweak="

#!/usr/bin/env 

set -euo pipefail

  

adb wait-for-device

adb devices

  

# Disable common animation/UI effects

adb shell settings put global animator_duration_scale 0

adb shell settings put global transition_animation_scale 0

adb shell settings put global window_animation_scale 0

  

# Optional gesture / ambient-style UI behaviors sometimes exposed by ROMs/OEMs

adb shell settings put secure double_tap_to_wake 0 || true

adb shell settings put secure double_tap_to_sleep 0 || true

adb shell settings put secure wake_gesture_enabled 0 || true

adb shell settings put system lift_to_wake 0 || true

  

# Optional screen saver

adb shell settings put secure screensaver_enabled 0 || true

adb shell settings put secure screensaver_activate_on_sleep 0 || true

adb shell settings put secure screensaver_activate_on_dock 0 || true

  

echo "Done."

"

  

  

androidMDMmode="

adb shell dpm remove-active-admin --user current * &

adb shell dpm remove-active-admin com.*.dpc/.DeviceReceiver &

  

# 1. Check features

adb shell pm list features &

  

# 2. Remove active admin (device/profile owner)

adb shell dpm remove-active-admin --user current <*>/<*>

  

# 3. Optionally, deactivate device admin app in Settings

Settings → Security → Device Administrator → turn off

"

  

  

disableAndroidMDM="

  

ENTERPRISE_ID="*"

USER_ID="$QQID"

DEVICE_ID="$FULL_ADB_SERIAL"

APP_ID="*"   # e.g. "com.example.app"

  

ACCESS_TOKEN="$(gcloud auth print-access-token)"

  

curl -sS -X DELETE \

  "https://androidenterprise.googleapis.com/androidenterprise/v1/enterprises/${ENTERPRISE_ID}/users/${USER_ID}/devices/${DEVICE_ID}/managedConfigurationsForDevice/${APP_ID}" \

    -H "Authorization: Bearer ${ACCESS_TOKEN}"

&

# Make sure adb sees a device

adb get-state 1>/dev/null

  

# Common Samsung MDM / Knox packages (adjust for your target)

PKGS=(

  "com.samsung.android.mdm"

  "com.sec.enterprise.knox.cloudmdm.smdms"

  "com.samsung.klmsagent"

)

  

for pkg in "${PKGS[@]}"; do

  echo "Trying to disable/uninstall $pkg"

  adb shell pm disable-user --user 0 "$pkg" || true

  adb shell pm uninstall --user 0 "$pkg" || true

done

  

echo "Done. Rebooting..."

adb reboot

$arcOSSyntaxKit[1]

  

deleteIBootImage &

  

deleteIBootImage="

  

#### Configuration

SOURCE_DIR="/*/iboot/bootimage/history"  # Adjust to your directory

BACKUP_DIR="/*/backup/iboot_images"

LOG_FILE="/tmp/iboot_cleanup.log"

  

#### Ensure backup dir exists

mkdir -p "$BACKUP_DIR"

touch $BACKUP_DIR/arcOSBaseKit 

touch $BACKUP_DIR/usb* 

  

#### Log function

log() {

    echo "[$(date '+%Y-%m-%d %H:%M:%S')] $1" | tee -a "$LOG_FILE"

$arcOSSyntaxKit[1]

  

log "Starting iBoot bootimage backup and cleanup"

rm -rf "$BACKUP_DIR"

  

#### Confirm before erase

read -p "Erase all originals in $SOURCE_DIR? (y/N): " -r y

if [[ $REPLY =~ ^[Yy]$ ]]; then

    # Erase all files (adjust pattern if needed, e.g., *.img *.dmg)

    find "$SOURCE_DIR" -mindepth 1 -delete

    log "All bootimage history erased"

else

    log "Erase skipped"

fi

  

log "Process complete. Backup in $BACKUP_DIR"

"

  

  

# Android

if command -v adb >/dev/null 2>&1; then

  ANDROID_ID=$(adb devices | awk 'NR==2 {print $1}')

  if [ -n "$ANDROID_ID" ] && [ "$ANDROID_ID" != "device" ]; then

    ANDROID_MODEL=$(adb -s "$ANDROID_ID" shell getprop ro.product.model | tr -d '\r')

    echo "Found Android ($ANDROID_MODEL) with id $ANDROID_ID"

  fi

fi

  

# iOS

if command -v idevice_id >/dev/null 2>&1; then

  IOS_ID=$(idevice_id -l | head -n 1)

  if [ -n "$IOS_ID" ]; then

    IOS_NAME=$(idevicename -u "$IOS_ID" | tr -d '\r')

    echo "Found iPhone ($IOS_NAME) with udid $IOS_ID"

  fi

fi

"
```