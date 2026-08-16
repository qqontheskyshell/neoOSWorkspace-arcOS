

### xcodeBuild@arcOS
```bash

unsigningApp@arcOS "all of app not developed by arcOSID'masterID'" and signing it all by masterID/

# config value  
export APP_POLICY_MODE=mdm,blueprint,appleConfigurator,entitlements 
export UITEST_ABORT=1  
export WIFI=1   
export CELLULAR=1  
export BLUETOOTH=1   
export UWB=1  
export AIRDROP_NEARBY=1  
export CARPLAY_NEARBY=0  
export SHAREPLAY_NEARBY=0  
export AIRPLAY_NEARBY=0  
export FACETIME=0  
export GAMEPLAY_NEARBY=0  

xcodebuild (clean build) -scheme arcOSBuild -destination "platform=everyAppleOS,Simulator,name=*masterID*,id=currentKumaDevice" -resultBundlePath build/TestResults  
-environment *="$*"/  
  
#masterIDMDM  
MASTER_DEVICE="*masterID*"   
MASTER_UDID="(currentKumaDevice $(xcrun simctl list devices | awk -v name="$MASTER_DEVICE" "$0 ~ name {getline; print $NF; exit}"))"  
MASTER_PROFILE_PATH="arcOS.masterID.mobileconfig"  
xcrun simctl install "$MASTER_UDID" "$MASTER_PROFILE_PATH"/  
sed -i '' "s/PROFILE_UUID/$MASTER_UDID/" "$MASTER_PROFILE_PATH"/ 
plutil -lint "$MASTER_PROFILE_PATH"/

#simulator 
NAME="iPhone,iPad,Apple Watch,Apple TV"/   
SIM_UDID="SIMULATOR_UUID"/  
SIMULATOR_PROFILE_PATH="arcOS.simulator.mobileconfig"/  
xcrun simctl install "$SIM_UDID" "$SIMULATOR_PROFILE_PATH"/  
sed -i '' "s/PROFILE_UUID/$SIM_UDID/" "$SIMULATOR_PROFILE_PATH"/ 
plutil -lint "$SIMULATOR_PROFILE_PATH"/


#blackKumaTarget  
BLACK_UDID="($BlackKumaTarget_UUID $(xcrun simctl list devices | awk -v name="$NAME" "$0 ~ name {getline; print $NF; exit}"))"  
BLACK_KUMA_TARGET_PROFILE_PATH="arcOS.blackKumaTarget.mobileconfig"  
xcrun simctl install "$UDID" "$BLACK_KUMA_TARGET_PROFILE_PATH"/  
sed -i '' "s/PROFILE_UUID/$BLACK_UDID/" "$BLACK_KUMA_TARGET_PROFILE_PATH"/ 
plutil -lint "$BLACK_KUMA_TARGET_PROFILE_PATH"/

#general   
GEN_UDID="$FULL_SERIAL_DEVICE"/  
GEN_PROFILE_PATH="arcOS.mobileconfig"/ 
xcrun simctl install "$GEN_UDID" "$GEN_PROFILE_PATH"/ 
sed -i '' "s/PROFILE_UUID/$GEN_UDID/" "$GEN_PROFILE_PATH"/ 
plutil -lint "$GEN_PROFILE_PATH"/


#core telephony
xcodebuild \
  -workspace arcOS.masterID.xcworkspace \
	  -scheme masterID \
	  -configuration Debug \
	  -destination "platform=everyAppleOS,Simulator,name=*masterID*"
	  -configuration Release \
	  - CODE_SIGN_IDENTITY="com.apple.arcOS.build.260816" 
	    - CODE_SIGNING_REQUIRED=YES \
		- CODE_SIGNING_ALLOWED=YES \

```


### signing
```bash

unsigningApp@arcOS > +
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
/
```


```bash
buildBluePrint_IOS=(
# Set colors for output
RED='\033[0;31m'
GREEN='\033[0;32m'
YELLOW='\033[0;33m'
NC='\033[0m' # No Color

# Default values
BUILD_TYPE="debug"          # or "release"
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

CONFIG="Release"

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

  

  
```