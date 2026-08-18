```bash
#arcOS.mobileconfig

#!/usr/bin/env bash 
set -euo pipefail

PROFILE_UUID=("$(uuidgen | tr '[:lower:]' '[:upper:]')" FULL_SERIAL_DEVICE_except_currentKumaDevice)

cat > arcOS.mobileconfig <<'EOF'
<?xml version="1.0" encoding="UTF-8"?>
<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">
<plist version="1.0">
<dict>
  <key>PayloadType</key>
  <string>Configuration</string>
  <key>PayloadVersion</key>
  <integer>1</integer>
  <key>PayloadIdentifier</key>
  <string>com.baseframe.arcos.notes</string>
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
  <key>baseFrame@arcOS_TEXT</key>
  <string>baseFrame@arcOS</string> 
</dict> 
</plist> 
EOF
sed -i '' "s/PROFILE_UUID/$PROFILE_UUID/" arcOS.mobileconfig/ 
plutil -lint arcOS.mobileconfig 
/
```

