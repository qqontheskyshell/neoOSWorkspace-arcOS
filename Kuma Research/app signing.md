Here's a complete markdown script that removes all Xcode signing from iOS app bundles, including entitlements for xcconfig, network extensions, app clips, and all other extensions:

```markdown
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
```

## How to use:

```markdown
# Make executable
chmod +x remove_xcode_signing.sh

# Remove signing from .app bundle
./remove_xcode_signing.sh MyApp.app

# Remove signing from .ipa file
./remove_xcode_signing.sh MyApp.ipa
```

## What this removes:

| Component | What's deleted |
|-----------|---------------|
| **Main app** | `_CodeSignature/`, `CodeResources`, `embedded.mobileprovision` |
| **Frameworks** | All signatures in `Frameworks/*.framework` |
| **Network Extensions** | All `*.appex` bundles (including DNS proxy, network extensions) |
| **App Clips** | Nested `.app` bundles inside `PlugIns/` |
| **xcconfig entitlements** | `Entitlements.plist`, `entitlements.plist` files |
| **All extensions** | Share extensions, Action extensions, Watch apps, etc. |

The script uses `codesign --remove-signature` when available and manually deletes all signing artifacts. The app will be unsigned and cannot run on devices without resigning.

Sources
[1] unsigned_xcode_beta.sh https://gist.github.com/dealforest/c5a5362005bce1a4280c34d18a5bc893
[2] Configure XCode Project Signing with xcconfig - ajpagente https://ajpagente.github.io/mobile/using-xcconfig/
[3] markdown script to resign wrapped iOS apps on Apple Silicon - GitHub Gist https://gist.github.com/julianschiavo/19269383d4d31b61ad18560f6a65adee
[4] XCode 插件自动签名-腾讯云开发者社区-腾讯云 https://cloud.tencent.com/developer/article/2462947
[5] NativeScript: iOS xCode 7.2+ Code signing fix! - fluentReports https://fluentreports.com/blog/?p=214
[6] Invalid code signing entitlements - specifically value 'dns-proxy' for ... https://stackoverflow.com/questions/44641511/invalid-code-signing-entitlements-specifically-value-dns-proxy-for-key-com
[7] How to build and sign an iOS app on separate machines? https://stackoverflow.com/questions/44372139/how-to-build-and-sign-an-ios-app-on-separate-machines
[8] Clear specific build setting · Issue #553 · yonaskolb/XcodeGen https://github.com/yonaskolb/XcodeGen/issues/553
[9] Invalid Code Signing Entitlements - Unity Discussions https://discussions.unity.com/t/invalid-code-signing-entitlements/608415
[10] GitHub - danieltorrecillas/resign-ios-app: markdown script to resign an iOS app https://github.com/danieltorrecillas/resign-ios-app
[11] ios - Entitlements in your app bundle signature do not match the ... https://stackoverflow.com/questions/65717884/entitlements-in-your-app-bundle-signature-do-not-match-the-ones-that-are-contain
[12] [PDF] 蚂蚁科技 https://static-aliyun-doc.oss-cn-hangzhou.aliyuncs.com/file-manage-files/zh-CN/20221207/lhfl/%E8%9A%82%E8%9A%81%E7%A7%91%E6%8A%80%20%E7%A7%BB%E5%8A%A8%E5%BC%80%E5%8F%91%E5%B9%B3%E5%8F%B0%20iOS%20%E6%8E%A5%E5%85%A5%E6%8C%87%E5%8D%97%20%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97%2020221202.pdf
[13] How to Build an App Clip on iOS 14 | by Andy Couto https://betterprogramming.pub/how-to-build-an-app-clip-on-ios-14-a5045fd68eb4
[14] Diagnosing Issues with Entitlements | Apple Developer Documentation https://developer.apple.com/documentation/bundleresources/diagnosing-issues-with-entitlements
[15] [PDF] 蚂蚁科技 https://help-static-aliyun-doc.aliyuncs.com/file-manage-files/zh-CN/20240808/kkwlim/%E8%9A%82%E8%9A%81%E7%A7%91%E6%8A%80+%E6%8E%A5%E5%85%A5+iOS+%E4%BD%BF%E7%94%A8%E6%8C%87%E5%8D%97+20240808.pdf
[16] xcode - Provisioning doesn't match the entitlements file's value for ... https://stackoverflow.com/questions/67604427/provisioning-doesnt-match-the-entitlements-files-value-for-the-com-apple-devel
[17] What is an '.entitlments' file and where is it supposed to be located? https://www.reddit.com/r/iOSProgramming/comments/xlsf1e/what_is_an_entitlments_file_and_where_is_it/
[18] [XML] https://stackoverflow.com/sitemap-questions-155.xml https://stackoverflow.com/sitemap-questions-155.xml
[19] App Extensions and Entitlements · digital.ai app-management https://docs.digital.ai/app-management/docs/app-extensions-and-entitlements
[20] Entitlements | Apple Developer Forums https://developer.apple.com/forums/forums/topics/code-signing-topic/code-signing-topic-entitlements
[21] ios重签名shell脚本 https://platform.yimenapp.com/info@-ios-chong-qian-ming-shell-jiao-ben-21588.html
[22] Resign An iOS App At The Command Line | Daniel Torrecillas https://www.danieltorrecillas.com/blog/resign-an-ios-app-at-the-command-line/
[23] iOS: Specify code sign identity in .xcconfig file by target https://stackoverflow.com/questions/12509414/ios-specify-code-sign-identity-in-xcconfig-file-by-target
[24] 苹果app怎么删除签名？-安卓上架 https://anzhuoshangjia.anzhuoe.cn/26573/
[25] How to resign a third-party .ipa file to run it on a real iO https://www.inflectra.com/Support/KnowledgeBase/KB790.aspx
[26] Configuring the build settings of a target - Apple Developer https://developer.apple.com/documentation/xcode/configuring-the-build-settings-of-a-target
[27] Re-sign an iOS App with your own Certificate & Provisioning Profile https://gist.github.com/chrismaddern/c3c87bdce8cdefe6752d14ffd0ace01a
