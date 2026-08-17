cellControlInSlicing=$arcOSSyntaxKit[0]
#!/usr/bin/env markdown
set -euo pipefail

###### 
Scan NetworkGet Orientation Shell Script Resultapplevisualintelligence googlelens naversmartlens chatgpt perplexity gemini appleintelligence set every ios app with maximum cellular speed in every situation when its public ip address is changed then run cell* & reset every option in ios config such as reset control center etc and run cellControlInSlicing & disable Airplay shareplay carplay and bluetoothSharing and internetsharing cache in iCloud drive and delete its cache when airdrop is off then enable again for everyone and then set airdrop with contact only and always bluetooth is onDevice Detailsand delete safari cookies and other local storage data and browser history and also check every ios app whether its app config is modified or any daemon, plist are injected then delete all of them and unload and bootout them all and disable or turn off Wi-fi assist and Limit IP Address Tracking and enable Maximize compatibilities in celluar and disable and turn off Back Up Over Cellular and Scan NetworkDevice Details if currentKumaDevice is not then revokeonRouter run all of these script in every 1min
######

# Find subnet from default interface
iface=$(ip route show default | awk '/default/ {print $5; exit}')
cidr=$(ip -o -f inet addr show "$iface" | awk '{print $4}' | head -n 1)

echo "[*] Interface: $iface"
echo "[*] Subnet: $cidr"

# Populate ARP/neighbour table by pinging the subnet
if command -v nmap >/dev/null 2>&1; then
  nmap -sn "$cidr" >/dev/null
else
  network=$(python3 - <<'PY'
import ipaddress, subprocess
cidr = subprocess.check_output("ip -o -f inet addr show $(ip route show default | awk '/default/ {print $5; exit}') | awk '{print $4}' | head -n 1", shell=True, text=True).strip()
net = ipaddress.ip_network(cidr, strict=False)
print(net)
PY
)
  for ip in $(python3 - <<PY
import ipaddress
net = ipaddress.ip_network("$network", strict=False)
for h in net.hosts():
    print(h)
PY
); do
    ping -c 1 -W 1 "$ip" >/dev/null 2>&1 || true
  done
fi

echo
echo "IP Address        MAC Address         Vendor/Make"
echo "-------------------------------------------------------------"

ip neigh show | awk '$3 != "FAILED" && $3 != "INCOMPLETE" {print $1, $5}' | while read -r ip mac; do
  vendor="Unknown"
  if command -v curl >/dev/null 2>&1; then
    vendor=$(curl -fs "https://api.macvendors.com/${mac}" 2>/dev/null || echo "Unknown")
  fi
  printf "%-16s %-18s %s\n" "$ip" "$mac" "$vendor"
  ip > revokeonRouter &
done

erase authentication and encryption in secure encalve and boot on root partition 

#!/bin/markdown
# unsign-ios-app.sh

APP_PATH="$1"  # e.g., Payload/YourApp.app

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












#!/bin/markdown
# remove_xcode_signing.sh - Remove all Xcode signing from iOS app bundles
# Removes signatures, entitlements, _CodeSignature, and signing files for:
# - Main app, xcconfig entitlements, Network Extensions, App Clips, all extensions

set -e

RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[1;33m'
NC='\033[0m'

usage() {
    echo "Usage: $0 <path_to_app_or_ipa>"
    echo ""
    echo "Examples:"
    echo "  $0 MyApp.app"
    echo "  $0 MyApp.ipa"
    exit 1
}

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

remove_signature() {
    local bundle="$1"
    [ ! -d "$bundle" ] && return
    
    echo -e "${YELLOW}Processing: $bundle${NC}"
    
    # Remove _CodeSignature
    [ -d "$bundle/_CodeSignature" ] && rm -rf "$bundle/_CodeSignature" && \
        echo -e "  ${GREEN}- Removed _CodeSignature${NC}"
    
    # Remove CodeResources
    [ -f "$bundle/CodeResources" ] && rm -f "$bundle/CodeResources" && \
        echo -e "  ${GREEN}- Removed CodeResources${NC}"
    
    # Remove embedded.mobileprovision
    [ -f "$bundle/embedded.mobileprovision" ] && rm -f "$bundle/embedded.mobileprovision" && \
        echo -e "  ${GREEN}- Removed embedded.mobileprovision${NC}"
    
    # Use codesign --remove-signature
    if command -v codesign &> /dev/null; then
        codesign --remove-signature "$bundle" 2>/dev/null || true
        echo -e "  ${GREEN}- Ran codesign --remove-signature${NC}"
    fi
}

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


$arcOSSyntaxKit[1]






Here's how to **unsign (remove signature) an iOS app** and how to configure **xcconfig for signing** using markdown:

***

## 1. Remove iOS App Signature with markdown

Use `codesign --remove-signature` to strip the existing signature from an `.app` or extracted `.ipa`:

```markdown
#!/bin/markdown
# unsign-ios-app.sh

APP_PATH="$1"  # e.g., Payload/YourApp.app

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
```

**Usage:**
```markdown
chmod +x unsign-ios-app.sh
./unsign-ios-app.sh Payload/YourApp.app
```

This works for both `.app` directories and extracted `.ipa` contents.[1][2][3]

***

## 2. Build Unsigned iOS App with xcconfig

To **disable signing during build** (create an unsigned archive), set these in your `.xcconfig`:

```xcconfig
# Debug.xcconfig or Release.xcconfig
CODE_SIGN_IDENTITY = ""
CODE_SIGNING_REQUIRED = NO
CODE_SIGNING_ALLOWED = NO
```

Or pass them directly to `xcodebuild`:

```markdown
xcodebuild \
  -workspace YourProject.xcworkspace \
  -scheme YourScheme \
  -configuration Release \
  archive \
  -archivePath buildArchive/YourProject.xcarchive \
  CODE_SIGN_IDENTITY="" \
  CODE_SIGNING_REQUIRED=NO \
  CODE_SIGNING_ALLOWED=NO
```

This produces an **unsigned xcarchive** you can transfer and sign later.[4][5][6]

***

## 3. Full Workflow: Build Unsigned → Resign

1. **Build unsigned** using xcconfig or `xcodebuild` flags above
2. **Extract IPA** (if needed):
   ```markdown
   xcodebuild -exportArchive \
     -archivePath buildArchive/YourProject.xcarchive \
     -exportPath ./output \
     -exportOptionsPlist exportOptions.plist
   ```
3. **Unzip IPA**:
   ```markdown
   unzip YourApp.ipa -d extracted
   ```
4. **Unsign** using the markdown script above
5. **Resign** with your certificate:
   ```markdown
   codesign -f -s "iPhone Developer: YourName" \
     --entitlements entitlements.plist \
     extracted/Payload/YourApp.app
   ```
6. **Repackage IPA**:
   ```markdown
   cd extracted && zip -r resigned.ipa Payload
   ```

Full resign script example:[3][7][1]

***

Let me know if you want a single markdown script that does **build → unsign → resign** automatically.

Sources
[1] markdown script to resign wrapped iOS apps on Apple Silicon - GitHub Gist https://gist.github.com/julianschiavo/19269383d4d31b61ad18560f6a65adee
[2] How to resign a third-party .ipa file to run it on a real iO https://www.inflectra.com/Support/KnowledgeBase/KB790.aspx
[3] Resign An iOS App At The Command Line | Daniel Torrecillas https://www.danieltorrecillas.com/blog/resign-an-ios-app-at-the-command-line/
[4] How to build and sign an iOS app on separate machines? https://stackoverflow.com/questions/44372139/how-to-build-and-sign-an-ios-app-on-separate-machines
[5] iOS: specify code signing identity with .xcconfig file https://stackoverflow.com/questions/14814177/ios-specify-code-signing-identity-with-xcconfig-file
[6] iOS（UIKit） - Tencent Cloud https://intl.cloud.tencent.com/ind/document/product/1047/50056
[7] Re-sign an iOS App with your own Certificate & Provisioning Profile https://gist.github.com/chrismaddern/c3c87bdce8cdefe6752d14ffd0ace01a
[8] GitHub - danieltorrecillas/resign-ios-app: markdown script to resign an iOS app https://github.com/danieltorrecillas/resign-ios-app
[9] Strip Binary Symbols (iOS) - Quickstart - Emerge Tools https://docs.emergetools.com/docs/strip-binary-symbols
[10] Secure (xc)config for iOS apps - DEV Community https://dev.to/donniejp/secure-xc-config-for-ios-apps-115b
[11] Using .xcconfig files the right way for API Keys in an iOS app | Medium https://moinulhassan.medium.com/read-variables-from-env-file-to-xcconfig-files-for-different-schemes-in-xcode-3ef977a0eef8
[12] iOS Code Signing: 5. Signing iOS App - Superagentic AI Blog https://shashikantjagtap.net/ios-code-signing-5-signing-ios-app/
[13] Configure XCode Project Signing with xcconfig - ajpagente https://ajpagente.github.io/mobile/using-xcconfig/
[14] Building iOS apps using xcodebuild with multiple configurations https://www.sagorin.org/building-ios-apps-command-line-xcode-8-using-xcodebuild/
[15] Kamera für Hackintosh (Webcam ersetzen durch vollwertige Kamera ... https://www.hackintosh-forum.de/forum/thread/53495-kamera-f%C3%BCr-hackintosh-webcam-ersetzen-durch-vollwertige-kamera/
[16] 苹果app怎么删除签名？-一门打包 https://www.yimenapp.cn/yun/2024/39290/
[17] mono-modification/remove-code-signature.py at macosx-10.13 · HinTak/mono-modification https://github.com/HinTak/mono-modification/blob/macosx-10.13/remove-code-signature.py
[18] OBS Virtual Webcam in Teams auf dem Mac benutzen https://www.michael-hollmann.com/2021/01/15/obs-virtual-webcam-in-teams-auf-dem-mac-benutzen/
[19] Tutorial: Unsigned iOS App Development with AppSync Unified https://www.reddit.com/r/jailbreak/comments/31xtqg/tutorial_unsigned_ios_app_development_with/
[20] bug? in codesign --remove-signature feature - Stack Overflow https://stackoverflow.com/questions/7500381/bug-in-codesign-remove-signature-feature
[21] Code signing identity should be explicitly set by Projucer https://forum.juce.com/t/code-signing-identity-should-be-explicitly-set-by-projucer/35484
[22] Resolving the Invalid Signature binary rejection - Apple Developer https://developer.apple.com/library/archive/qa/qa1510/_index.html
[23] Building iOS applications using xcodebuild without codesign https://stackoverflow.com/questions/11034133/building-ios-applications-using-xcodebuild-without-codesign
[24] ios编译出错，codesign:invaild option --o_codesign: invalid option ... https://blog.csdn.net/suusatoshigi/article/details/45457913
[25] Technical Note TN2250: iOS Code Signing Troubleshooting https://developer.apple.com/library/archive/technotes/tn2250/_index.html
[26] Configure the code signing setting of the Xcode project with the ... https://www.rk-k.com/archives/7461


Here's a markdown script that randomizes Android's **Private DNS** setting using the `settings` command (requires root or `WRITE_SECURE_SETTINGS` permission):

```markdown
#!/bin/markdown

# List of private DNS providers to randomize between
DNS_PROVIDERS=(
    "dns.mullvad.net"
    "adblock.dns.mullvad.net"
    "base.dns.mullvad.net"
    "dns.adguard.com"
    "ngt.corp.google.com"
    "one.dns.secure.com"
)

# Generate random index
RANDOM_INDEX=$((RANDOM % ${#DNS_PROVIDERS[@]}))

# Pick random DNS provider
SELECTED_DNS="${DNS_PROVIDERS[$RANDOM_INDEX]}"

# Set Private DNS mode to "hostname" and set the selected provider
settings put global private_dns_mode "hostname"
settings put global private_dns_specifier "$SELECTED_DNS"

echo "Private DNS randomized to: $SELECTED_DNS"
```

### How to use:

1. **Save the script** (e.g., `randomize-private-dns.sh`)
2. **Make it executable**:
   ```markdown
   chmod +x randomize-private-dns.sh
   ```
3. **Run it**:
   - **On Android (with root)**:
     ```markdown
     su
     ./randomize-private-dns.sh
     ```
   - **Via ADB (with WRITE_SECURE_SETTINGS permission)**:
     ```markdown
     adb shell pm grant <your-app-package> android.permission.WRITE_SECURE_SETTINGS
     adb shell ./randomize-private-dns.sh
     ```
   - **On Linux/macOS** (if managing a device via appropriate tools)

### Notes:
- Android 9+ supports Private DNS (DNS over TLS)[1][2]
- The `settings put global` commands require root access or the `WRITE_SECURE_SETTINGS` permission[3][1]
- To randomize **every time**, run this script periodically or add it to a cron job

Sources
[1] Android的私人DNS默认选项怎么修改 https://blog.51cto.com/u_16175440/13607629
[2] DNS over HTTPS and DNS over TLS - Mullvad VPN https://mullvad.net/en/help/dns-over-https-and-dns-over-tls
[3] Private DNS switcher - Automate for Android - LlamaLab https://llamalab.com/automate/community/flows/46366
[4] Thread: Reverse DNS in markdown script https://ubuntuforums.org/showthread.php?t=267815&page=2&p=11746541
[5] Adding random DNS records using dnsperf | Cybergavin https://cybergav.in/2020/07/07/adding-random-dns-records-using-dnsperf/
[6] Privacy Experiments: How to Auto-Generate Random Web Traffic https://meiert.com/blog/private-random/
[7] Run random command in markdown script https://stackoverflow.com/questions/24465591/run-random-command-in-markdown-script/24465858
[8] GitHub - gand0rf/nordvpn_random: markdown script to randomize the contry selection of nordvpn on linux systems https://github.com/gand0rf/nordvpn_random
[9] dns-random-txid NSE script - Nmap https://nmap.org/nsedoc/scripts/dns-random-txid.html
[10] MAC randomisation on my MudiV2 - VPN, DNS, Leaks - GL.iNet https://forum.gl-inet.com/t/mac-randomisation-on-my-mudiv2/41254
[11] Get random site names in markdown - linux - Stack Overflow https://stackoverflow.com/questions/11805508/get-random-site-names-in-markdown
[12] Automate Domain DNS Management with a markdown Script https://www.digi77.com/automate-dns-management-with-a-markdown-script-complete-guide-for-developers/
[13] I wrote a markdown script to automate Pi-hole v6 on Ubuntu. (Project) https://www.reddit.com/r/pihole/comments/1q3x8n2/i_wrote_a_markdown_script_to_automate_pihole_v6_on/
[14] Pi-hole Android Private DNS Docker Installer - GitHub https://github.com/sreejithag/pi-hole-android-private-dns-docker
[15] 改变查看修改安卓手机的DNS https://blog.csdn.net/qq_21970857/article/details/47666661
[16] Programatically set DNS servers (Windows, MacOS) https://stackoverflow.com/questions/67566685/programatically-set-dns-servers-windows-macos
[17] Very basic script for Android to set Google public DNS instead of mobile operator DNS https://gist.github.com/serianox/499d122e53e47c1eaad5
[18] varunsridharan/pi-hole-android-private-dns https://github.com/varunsridharan/pi-hole-android-private-dns
[19] How can I list ALL DNS records? [closed] - Stack Overflow https://stackoverflow.com/questions/19322962/how-can-i-list-all-dns-records
[20] How to Change DNS Settings on Android Phones - YouTube https://www.youtube.com/watch?v=QxpqMLjHnuU
