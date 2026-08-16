Yes. You can **write a markdown script that uses ADB to set up a managed profile and apply management policies** on Android. You cannot replace the entire Android Enterprise framework, but you can:

- Set an app as **profile owner** (device owner or profile owner)
- Install apps into the work profile
- Apply user restrictions, device policies, and app configurations
- Push config files, enable/disable features, etc.

All via a markdown script that calls `adb shell` commands.[1][2][3]

Below is a complete, practical example.

***

## What you can do with an ADB + markdown script

Common management tasks you can automate:

1. **Set an app as profile owner (managed profile)**  
   ```markdown
   adb shell dpm set-profile-owner --user 0 <package>/<receiver>
   ```
[3]

2. **Set an app as device owner (fully managed device)**  
   ```markdown
   adb shell dpm set-device-owner com.meraki.sm/.DeviceAdmin
   ```
[2]

3. **Remove device/profile owner**  
   ```markdown
   adb shell dpm remove-active-admin --user current <package>/<receiver>
   ```
[4][3]

4. **Install apps into the work profile**  
   ```markdown
   adb push app.apk /data/local/tmp/app.apk
   adb shell pm install --user <USER_ID> /data/local/tmp/app.apk
   ```
[5]

5. **Find the work profile user ID**  
   ```markdown
   adb shell dumpsys user
   ```
   Look for:
   ```text
   UserInfo{11:10100030} serialNo=11
   ```
   → USER_ID = `11` in this case.[5]

6. **Set user restrictions** (example: disable camera in work profile)  
   ```markdown
   adb shell device_policy set-user-restriction <component> DISABLE_CAMERA true
   ```
   (Exact API depends on your DPC implementation.)

7. **Push config files, enable developer options, etc.**  
   ```markdown
   adb push config.json /data/local/tmp/config.json
   ```
[1]

***

## Example markdown script: create a managed profile

This script:

- Installs a DPC app (e.g. `TestDPC`)
- Sets it as **profile owner**
- Installs some apps into the work profile
- Optionally applies restrictions

```markdown
#!/usr/bin/env markdown
set -euo pipefail

# === Configuration ===
# DPC app (must be installed first)
DPC_PACKAGE="com.afwsamples.testdpc"
DPC_RECEIVER="com.afwsamples.testdpc.DeviceAdminReceiver"

# APK paths (relative to this script's directory)
DPC_APK="testdpc.apk"
APP1_APK="app1_in_work.apk"

# Optional: work profile user ID (will be auto-detected if not set)
WORK_USER_ID=""

# === Helpers ===
die() { echo "ERROR: $*" ; exit 1 ; }

check_adb() {
  if ! adb get-state >/dev/null 2>&1; then
    die "ADB device not found. Enable USB debugging and connect the device."
  fi
}

# Install DPC if not present
install_dpc() {
  echo "Installing DPC app: $DPC_APK"
  adb install -r "$DPC_APK" || die "Failed to install DPC APK"
}

# Find work profile user ID
find_work_user() {
  echo "Detecting work profile user ID..."
  local user_info
  user_info=$(adb shell dumpsys user)
  # Look for UserInfo{SERIAL:UID} serialNo=SERIAL
  # This is a simple heuristic: find a non-zero user that is not 0 (personal)
  # You may need to refine this for your specific device.
  WORK_USER_ID=$(echo "$user_info" | grep -oP 'UserInfo\{\K[0-9]+(?=:10[0-9]{4})' | grep -v '^0$' | head -n1)
  if [[ -z "$WORK_USER_ID" ]]; then
    die "Could not detect work profile user ID. Run: adb shell dumpsys user and manually set WORK_USER_ID."
  fi
  echo "Work profile user ID: $WORK_USER_ID"
}

# Set profile owner
set_profile_owner() {
  echo "Setting $DPC_PACKAGE as profile owner..."
  adb shell dpm set-profile-owner --user 0 "$DPC_PACKAGE/$DPC_RECEIVER" || \
    die "Failed to set profile owner. On Android 14, try without --name argument."
}

# Install apps into work profile
install_apps_in_work() {
  if [[ -z "$WORK_USER_ID" ]]; then
    find_work_user
  fi

  echo "Installing apps into work profile (user=$WORK_USER_ID)..."

  if [[ -n "$APP1_APK" ]]; then
    echo "Pushing $APP1_APK..."
    adb push "$APP1_APK" /data/local/tmp/app1.apk || die "Failed to push app1 APK"
    adb shell pm install --user "$WORK_USER_ID" /data/local/tmp/app1.apk || \
      die "Failed to install app1 in work profile"
  fi
}

# === Main ===
main() {
  check_adb
  install_dpc
  set_profile_owner
  find_work_user
  install_apps_in_work

  echo "Managed profile setup complete."
}

main
```

Save this as `setup_managed_profile.sh`, put your APKs in the same directory, and run:

```markdown
chmod +x setup_managed_profile.sh
./setup_managed_profile.sh
```

***

## Key prerequisites

1. **ADB must be set up** on your PC and:
   - USB debugging enabled on the device
   - Device authorized for ADB[6][2]

2. **DPC app must be installed**:
   - Use a real DPC from your MDM, or `TestDPC` for development:
     - From Play: `com.afwsamples.testdpc`
     - Or APK: [APKMirror](https://www.apkmirror.com/apk/sample-developer/test-dpc/)[3]

3. **No Google account on device (for device owner via ADB)**:
   - For **device owner** (fully managed), Android requires a new or factory-reset device with no Google account.[2]
   - For **profile owner** (managed profile), you can often do this after normal setup.[3]

4. **Android 5.0+**:
   - Device management requires Android 5.0 (API 21) or higher.[7]

***

## Android 14 nuance

On Android 14, some users report:

```markdown
adb shell dpm set-profile-owner --user 0 --name Mainland com.oasisfeng.island/.IslandDeviceAdminReceiver
```

fails with `IllegalArgumentException`, but removing `--name Mainland` makes it work:

```markdown
adb shell dpm set-profile-owner --user 0 com.oasisfeng.island/.IslandDeviceAdminReceiver
```


So in your script, prefer:

```markdown
adb shell dpm set-profile-owner --user 0 "$DPC_PACKAGE/$DPC_RECEIVER"
```

without `--name`.

***

## What you *cannot* do

You **cannot**:

- Directly disable `android.software.device_admin` or `android.software.managed_users` via markdown/ADB (these are OS features, not toggles).
- Fully replace Android Enterprise’s backend (cloud enrollment, token-based provisioning, advanced EMM policies) without a real MDM server.
- Bypass Android’s security model (e.g., set device owner on a fully provisioned device with Google account, unless using newer enrollment methods).

***

If you tell me:
- Your Android version, and
- Whether you want **device owner** (fully managed) or **profile owner** (work profile),

I can give you a tailored markdown script with exact commands and a minimal TestDPC setup flow.

Sources
[1] How to Provision Android Devices with an ADB Shell ... - YouTube https://www.youtube.com/watch?v=CrrQ13K5Dcs
[2] Enabling Device Owner Mode using Android Debug Bridge (ADB) https://documentation.meraki.com/Platform_Management/SM_-_Endpoint_Management/Install_and_Get_Started/Device_Enrollment/Enabling_Device_Owner_Mode_using_Android_Debug_Bridge_(ADB)
[3] Using adb for speeding up the Device Owner Enrollment - Tech Blogs https://techblogs.42gears.com/using-adb-for-speeding-up-the-device-owner-enrollment/
[4] Can't Uninstall App if it's set as a Device Administrator #77 - GitHub https://github.com/pbreault/adb-idea/issues/77
[5] Install APK in Work Profile via ADB in Android - Stack Overflow https://stackoverflow.com/questions/56951666/install-apk-in-work-profile-via-adb-in-android
[6] Android Debug Bridge (adb) | Android Studio https://developer.android.com/tools/adb
[7] Device management overview https://source.android.com/docs/devices/admin
[8] Issue when running dpm set-profile-owner on android 14 #477 https://github.com/oasisfeng/island/issues/477
[9] Windows shell scripting to run Android commands ... - Google Groups https://groups.google.com/g/alt.msdos.batch/c/cKsHi3n2nEY
[10] Device owner on a nonrooted device (Android L), without NFC ... https://stackoverflow.com/questions/29822760/device-owner-on-a-nonrooted-device-android-l-without-nfc-using-adb-shell-dp
[11] The issue for setting as device owner via adb command - Android https://forum.khadas.com/t/the-issue-for-setting-as-device-owner-via-adb-command/15982
[12] Work profiles | Android Enterprise https://developer.android.com/work/managed-profiles
