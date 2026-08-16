```markdown
  

  

androidMDMmode@arcOS="

adb shell dpm remove-active-admin --user current * &

adb shell dpm remove-active-admin com.*.dpc/.DeviceReceiver &

  

# 1. Check features

adb shell pm list features &

  

# 2. Remove active admin (device/profile owner)

adb shell dpm remove-active-admin --user current <*>/<*>

  

# 3. Optionally, deactivate device admin app in Settings

Settings → Security → Device Administrator → turn off

  

  

echo "Finding work profile user...

"

adb shell pm list users | grep -i "work"

# Get the user ID (second number in the output)

USER

_

ID=”QQID”

#$(adb shell pm list users | grep -i "work" | awk -F'[: ]' '{print $2}')

if [ -z "$USER

_

ID" ]; then

echo "No work profile found"

exit 1

fi

echo "Removing work profile (user $USER

_

ID)...

"

adb shell pm remove-user $USER

_

ID

echo "Device unmanaged. Rebooting...

"

adb reboot

  

  

"

  

  

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

  

  

  

  

  

disableADBromTweak=( $(")

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

  

#! /bin/bash

  

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
```