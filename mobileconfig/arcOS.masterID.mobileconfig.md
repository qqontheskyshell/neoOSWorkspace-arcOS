```bash
#arcOS.masterID.mobileconfig
masterMDM@arcOS > + 
#setting
StandBy > disable all of these/

#continuity
Airplay,CarPlay, SharePlay,Apple Advertising,Game Center > disable all of these/
AirDrop with Everyone in 1min > enable all/

#network
PrivateRelay,Hotspot,Calls on Other Devices > disable all of these/
Bluetooth > enable all/
Wifi > within currentKumaDevice, only QQ_WHT_IPHONE_17e wifi is always on others are off and wifi power is set as high and reckon with baseFrame@arcOS on arcOSQQLocalTarget/
Cellular set as cellMode with 5Gon with Allow More Data on 5G > reset Statistic in Cellular and Data usage,disable iCloud drive and sharingd cache/
Limit IP Address Tracking is on toggle mode/
Satellite > only on when it is 911@arcOS + default value will be off/
Location Service > MyLocation share as This Device/
FindMy > only by QQID@icloud.com > enable all/
FindNetwork only by QQID@icloud.com > enable all/
QQ_WHT_IPHONE_17e > cellMode + roaming is off/
QQ_ORNG_PRO > cellMode + when 911@arcOS is nearby masterID or his body or other location in the globe then set as satMode and once it is finished then roll back on cellMode/
QQ_BLK_IPAD_PRO > cellMode + roaming is off/

#accessibility
Dictation > disable all of these/
disable all Accessibility except LiveSpeak > 911@arcOS on masterID then set reducemotion is on + vehiclemotioncue is on with dynamic and change color as random value/
QQ_WHT_IPHONE_17e > setActionButton as speakscreen/
QQ_ORNG_PRO > setActionButton as accessibilityReader/

#hardware
front and back camera > disable all of these/

#system
ControlCenter > reset/
Notifications > screen sharing notification is on/
Keyboard as English, Korean/
Apple Intelligence/

#MDM
VPN & Device Management > disable all of these/
Screen Time > share across device within QQID@icloud.com + disable Bluetooth Sharing + Tracking > ask App stop to tracking/
+ Extentions > disable all of these/

#authentication
Face ID & Passcode > disable all section in Allow Access When Locked and voice dial/
AutoFill & Password > enable only when it used + disable Suggest Strong Passwords/

#iCloud
iCloud > every saved to iCloud is on + icloud.com access is on + Contact Key Verification is on/

#AI
Siri > disable Image creating, realistic creation, extentions/
/

/
#!/usr/bin/env bash 
set -euo pipefail

DAEMON_PREFIX="com.apple.arcOS"
YOUR_CARRIER_TRAFFIC_CATEGORY="*"
YOUR_CARRIER_APP_CATEGORY="*"
PROFILE_UUID=("$(uuidgen | tr '[:lower:]' '[:upper:]')" currentKumaDevice,kumaDeviceForWDS,EveryAppInsideOfiOS,EveryUIElementIniOS)
cat > arcOS.masterID.mobileconfig <<'EOF'
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>PayloadType</key>
  <string>Configuration</string>
  <key>PayloadVersion</key>
  <integer>1</integer>
  <key>PayloadIdentifier</key>
  <string>DAEMON_PREFIX.baseframe</string>
  <key>PayloadUUID</key>
  <string>__PROFILE_UUID__</string>
  <key>PayloadDisplayName</key>
  <string>baseFrame@arcOS Notes Profile</string>
  <key>PayloadOrganization</key>
  <string>baseFrame@arcOS</string>
  <key>PayloadDescription</key>
  <string>Stores custom configuration text for debugging/reference.</string>
  <key>PayloadContent</key>
  <array/>
  <key>masterMDM@arcOS_TEXT</key>
  <string>masterMDM@arcOS</string> 
</dict> 
<dict>
    <key>DAEMON_PREFIX.networking.slicingMDM</key>
    <array>
        <string>YOUR_CARRIER_APP_CATEGORY</string>
    </array>

    <key>DAEMON_PREFIX.networking.trafficMDM</key>
    <array>
        <string>YOUR_CARRIER_TRAFFIC_CATEGORY</string>
    </array>
</dict>
</plist> 
EOF

/
```