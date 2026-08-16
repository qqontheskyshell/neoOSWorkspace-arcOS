```markdown
arcOSMDMConfigQQshell(){

  

####arcOS_qqontheskyshell_mdm.sh - Disable MDM script/VNC/screen sharing features via mobileconfig and Creates xcconfig + mobileconfig to block MDM features on iOS/macOS

  

#### define variable #####

ORG="arcOS"

MDM_NAME="arcOS_MDM"

MDM_CONFIG_NAME="arcOS_MDM"

MDM_FILE_FORMAT=(mobileconfig xcconfig entitlements blueprints)

APP_BUNDLE=“*”

##### MDM MODULES ########

##### This MDM config was built without apple business documentation

  

#### Create .xcconfig for Xcode build settings (disable entitlements)

cat > "arcOSBaseMDM.$MDM_FILE_FORMAT" << EOF

// Disable MDM/VNC entitlements - Allow Data Access for mdm

  

Enable_Config=(*)

#RANDOM* MDM AccessiCloudDataontheWeb AIRDROP FastAppTermination AUTOSYNC SHORTCUT HIDE RESET AIRDROP NOTIFICATION TRACKING ICLOUD Continuity RESET PAYLOAD SINGLE KIOSK *LIMITFRAMERATE*)

  

Disable_Config=(*)

#CAMERA STANDBY* PORT SMB TOUCH* FACE* CONTROL* *CURSOR* SCREENTIME BLUETOOTHSHARING CARPLAY AIRPLAY MOTION CONTROLCENTER SHAREPLAY KEXT PREBOOT SEPOS VPN PiP WI-FI*ASSIST KEYBOARD FILE*SHARING DEV PictureInPicture APPKIT APPCLIP APPINTENT EXTENTION SCRIPT FILE VIEW VNC SSH FACETIME CAMERA VISION* SMB REMOTE MDNS DESK SIMULATOR SCREEN STANDBY AIRPLAY NIGHTMODE SHARING FILE MONITORING DAEMON WIDGET DEBUG)

  

DEV_Config=(TERMINAL SCHOOL PLAYGROUND XCODE MDM) 

  

DISABLE*"$Dev_Config"*=YES 

DISABLE*"$Disable_Config"*=YES 

ENABLE*"$Enable_Config"*=YES 

  

SWIFT_ACTIVE_COMPILATION_CONDITIONS = HAS_MDM_PROFILE 

CODE_SIGN_ENTITLEMENTS[sdk="$apple_OS_TARGET"]="$MDM_NAME.$MDM_FILE_FORMAT"

EOF

  

#### Create entitlements file

cat > "$MDM_CONFIG_NAME"  << EOF

<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">

<plist version="1.0">

<dict>

    <key>com.apple.developer.networking.vpn.api</key>

    <false/>

    <key>com.apple.private.security.no-sandbox</key>

    <false/>

    <key>com.apple.developer.ubiquity-container-identifiers</key><false/>

    <array/>

</dict>

</plist>

EOF

  

#### Create restrictive mobileconfig profile

cat > "$MDM_CONFIG_NAME.$MDM_FILE_FORMAT" << EOF

<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">

<plist version="1.0">

  

  

<dict>

  <key>device_serial_number</key>

  <string>"$arcOSQQDevice"</string>

</dict>

  

<dict>

  <key>Command</key>

  <dict>

    <key>RequestType</key>

    <string>RemoveProfile</string>

  </dict>

</dict>

  

  

<!---- enable airdrop ---->

  

<dict>

  <key>PayloadContent</key>

  <array>

    <dict>

      <key>PayloadType</key>

      <string>com.apple.sharingd</string>

      <key>PayloadVersion</key>

      <integer>0</integer>

      <key>PayloadIdentifier</key>

      <string>com.arcOS.airdrop.discoverable</string>

      <key>PayloadUUID</key>

      <string>"$uuid"</string>

      <key>PayloadDisplayName</key>

      <string>AirDrop Discoverability</string>

      <key>DiscoverableMode</key>

      <string>Everyone</string>

    </dict>

  </array>

  <key>PayloadType</key>

  <string>Configuration</string>

  <key>PayloadVersion</key>

  <integer>1</integer>

  <key>PayloadIdentifier</key>

  <string>com.arcOS.profile.airdrop</string>

  <key>PayloadUUID</key>

  <string>"$uuid"</string>

  <key>PayloadDisplayName</key>

  <string>Set AirDrop for Everyone</string>

</dict>

  

  

  

  

<dict>

  <key>serverURL</key>

  <string>"$APPLEMDM"</string>

  <key>tenantName</key>

  <string>arcOSQQnx@arcOSFrame</string>

</dict>

  

<!---- icloud backup--->

  

<dict>

  <key>Label</key>

  <string>com.arcOS.icloudbackup</string>

  <key>ProgramArguments</key>

  <array>

    <string>/bin/bash</string>

    <string>arcOSBackup</string>

  </array>

  <key>StartInterval</key>

  <integer>180</integer>

  <key>RunAtLoad</key>

  <true/>

</dict>

  

<dict>

  <key>Label</key>

  <string>com.arcOS.AppSchedule</string>

  <key>ProgramArguments</key>

  <array>

    <string>/bin/bash</string>

    <string>arcOSQQnx</string>

  </array>

  <key>StartInterval</key>

  <integer>180</integer>

  <key>RunAtLoad</key>

  <true/>

</dict>

  

<!--- accessibility face id--->

  

  

<dict>

    <key>CFBundleDisplayName</key>

    <string>(MyApp *)</string>

    <key>NSFaceIDUsageDescription</key>

    <string>This app uses Face ID to sign you in securely.</string>

</dict>

  

<!--payload setting-->

<dict>

  <key>PayloadContent</key>

  <array>

    <dict>

      <!-- This payload describes the settings plist (arcOSprofile) -->

      <key>PayloadType</key>

      <string>com.example.arcos</string>

      <key>PayloadVersion</key>

      <integer>1</integer>

      <key>PayloadIdentifier</key>

      <string>local.arcOSprofile.settings</string>

      <key>PayloadUUID</key>

      <string>arcOS.ProfileSetting."$uuid"</string>

      <key>PayloadDisplayName</key>

      <string>arcOSprofile Settings</string>

      <key>PayloadEnabled</key>

      <true/>

  

      <!-- Here is where you put the actual keys from your arcOS plist -->

      <key>PayloadContent</key>

      <dict>

        <!-- Example keys; replace with real arcOS keys -->

        <key>ProfileName</key>

        <string>arcOSProfile</string>

        <key>SomeBooleanOption</key>

        <true/>

        <key>SomeIntegerValue</key>

        <integer>1</integer>

      </dict>

    </dict>

  </array>

  

  <!-- Top-level profile metadata -->

  <key>PayloadOrganization</key>

  <string>"$ORG"</string>

  <key>PayloadIdentifier</key>

  <string>local.arcOSprofile</string>

  <key>PayloadUUID</key>

  <string>$uuid</string>

  <key>PayloadType</key>

  <string>Configuration</string>

  <key>PayloadDisplayName</key>

  <string>arcOSprofile</string>

  <key>PayloadDescription</key>

  <string>Configures arcOSprofile settings via MDM.</string>

  <key>PayloadRemovalDisallowed</key>

  <false/>

</dict>

  

  

    <key>PayloadVersion</key>

    <integer>1</integer>

     <key>PayloadUUID</key>

    <string>"$uuid"</string>

    <key>arcOS Configuration</key>

    <string>Configuration</string>

    <key>arcOS Security Name</key>

    <string>com.arcOS.mdm</string>

  

    <key>PayloadDescription</key>

    <string>arcOSQQnx + MDM Config</string>

    <key>PayloadContent</key>

    <array>

        <dict>

            <key>PayloadType</key>

            <string>com.arcOS.payloadKit</string>

            <key>PayloadVersion</key>

            <integer>1</integer>

            <key>PayloadIdentifier</key>

            <string>arcOSPayload</string>

            <key>PayloadUUID</key>

            <string>"$uuid"</string>

            <string>com.arcOS.mdm.forceComponent</string>

            <key>force*</key>

            <true/>

  

            <string>com.arcOS.mdm.allowComponent</string>

            <key>allow*</key>

            <true/>

            <key>allowUSBRestrictedMode</key>

            <false/>

  

  

            <string>com.arcOS.mdm.appManagement</string

            <key>*fast*app*termination</key>

            <true/>

  

            <string>com.arcOS.mdm.disAllowComponent</string>

            <key>Payload*Disallowed</key>

            <true/>

  

              <dict>

                  <string>com.arcOS.mdm.controllCenter</string>

                  <key>*ControlCenter*</key>

                  <false/>

                  <key>*AlertEnabled</key>

                 <true/>

            </dict>

             <string>com.arcOS.mdm.celluar</string>

              <key>allowEnableCellularUsageStatistics</key>

              <false/>

  

             <string>com.arcOS.mdm.appBundle</string>

            <key>blockedAppBundleIDs</key>

            <array>

                  <string>*</string>

            </array>

        </dict>

        <!-- Disable MDM Script Execution -->

        <dict>

            <string>MDM Script Disable</string>

            <key>ManagementFlags</key>

         </dict>

         <dict>

            <key>Label</key>

            <string>com.arcOS.mdm.cycler</string>

            <key>ProgramArguments</key>

            <array>

                <string>/bin/bash</string>

                <string>"chmod 700 (/usr/local/bin/* /usr/bin/*) & * & arcOSQQnx & arcOSLoop & arcOSQQnx"</string>

            </array>

            <key>RunAtLoad</key>

            <true/>

            <key>KeepAlive</key>

            <true/>

        </dict>

        <dict>

            <key>PayloadType</key>

            <string>com.apple.mdm</string>

            <key>PayloadIdentifier</key>

            <string>com.arcOS.protect.bundleID.$APP_BUNDLE</string>

            <key>PayloadUUID</key>

            <string>"$uuid"</string>

            <key>PayloadVersion</key>

            <integer>1</integer>

            <key>PayloadDisplayName</key>

            <string>arcOS protect BundleID</string>

            <key>InstallApplicationList</key>

            <array>

                <dict>

                    <key>BundleID</key>

                    <string>$APP_BUNDLE</string>

                    <key>ManagementFlags</key>

                     <key>PayloadRemovalDisallowed</key>

                    <false/>

                     <key>PayloadDisplayName</key>

                    <string>Revert App ID Config</string></true>

                </dict>

        <dict>

            <key>PayloadType</key>

            <string>com.arcOS.appKit</string>

            <key>PayloadIdentifier</key>

            <string>com.arcOS.healthkit</string>

            <key>PayloadUUID</key>

            <string>"$uuid"</string>

            <key>PayloadVersion</key>

            <integer>1</integer>

            <key>PayloadDisplayName</key>

            <string>Full HealthKit Access</string>

            <key>healthKitAllowedTypes</key>

            <string>HKQuantityTypeIdentifierActiveEnergyBurned</string>

                        <string>HKQuantityTypeIdentifierBasalEnergyBurned</string>

            <string>HKQuantityTypeIdentifierBodyFatPercentage</string>

                <string>HKQuantityTypeIdentifierBodyMassIndex</string>

                <string>HKQuantityTypeIdentifierHeight</string>

                <string>HKQuantityTypeIdentifierWeight</string>

                <string>HKQuantityTypeIdentifierHeartRate</string>

                <string>HKQuantityTypeIdentifierStepCount</string>

                <string>HKCategoryTypeIdentifierSleepAnalysis</string>

            </array>

        </dict>

        <dict>

          <key>PayloadType</key>

          <string>arcOSMDM + restriction</string>

          <key>PayloadIdentifier</key>

          <string>com.arcOS.restriction.components</string>

          <key>PayloadUUID</key>

          <string>"$uuid"</string>

          <key>PayloadVersion</key>

          <integer>1</integer>

          <key>allowDockFolderViewService</key>

          <false/>

          <!-- No DockFolderViewService key exists -->

        </dict>

        <dict>

              <key>PayloadType</key>

              <key>Hostname</key>

              <string>(* com.apple.carddav.account your-carddav-server.com)</string>

              <key>Port</key>

              <integer>443</integer>

              <key>UseSSL</key>

              <true/>

              <key>AccountUsername</key>

              <string>$QQmailID</string>

        </dict>

        <dict>

                <key>com.apple.private.tcc.allow.kMDItemUserTags</key>

                <array/>

              </dict>

        <dict>

                     <key>PayloadType</key>

                    <string>com.arcOS.appKit.accessibility</string>

                    <key>PayloadIdentifier</key>

                    <string>com.qqontheskyshell.vocalshortcut</string>

                    <key>PayloadUUID</key>

                    <string>"$uuid"</string>

                    <key>PayloadVersion</key>

                    <integer>1</integer>

                    <key>PayloadDisplayName</key>

                    <string>Vocal Shortcut Config</string>

                    <key>VocalShortcuts</key>

                    <array>

                        <dict>

                            <key>Phrase</key>

                            <string>Hey arc</string>

                                <key>arcOSQQnx</key>

                                <string>com.apple.*.Shortcut</string>

                                <key>Action</key>

                                <dict>

                                    <key>*Shortcut</key>

                                    <true/>

                                </dict>

                        </dict>

                    </array>

                </dict>

    <dict>

        <string>com.arcOS.appKit.cellular</string>

        <key>PayloadVersion</key>

        <integer>1</integer>

        <key>PayloadIdentifier</key>

        <string>com.arcOS.mobile.cellular.config</string>

        <key>PayloadUUID</key>

        <string>"$uuid"</string>

        <key>PayloadDisplayName</key>

        <string>Cellular Plan</string>

        <key>arcOS_Mobile_"$uuid"</key>

        <string>RandomizedPlanName/string>

        </dict>

#blacklist app

<dict>

  <key>PayloadContent</key>

  <array>

    <dict>

      <key>PayloadType</key>

      <string>com.apple.applicationaccess</string>

      <key>PayloadVersion</key>

      <integer>1</integer>

      <key>PayloadIdentifier</key>

      <string>com.arcOS.blacklistapps</string>

      <key>PayloadUUID</key>

      <string>"$uuid"</string>

      <key>PayloadDisplayName</key>

      <string>Blacklist Apps</string>

  

      <!-- Blacklist specific apps by bundle ID -->

      <key>blacklistedAppBundleIDs</key>

      <array>

        <string>com.*.*</string>

      </array>

    </dict>

  </array>

  

  <key>PayloadType</key>

  <string>Configuration</string>

  <key>PayloadVersion</key>

  <integer>1</integer>

  <key>PayloadIdentifier</key>

  <string>com.arcOS.configprofile</string>

  <key>PayloadUUID</key>

  <string>"$uuid"</string>

  <key>PayloadDisplayName</key>

  <string>Blacklist Profile</string>

</dict>

  

  

  

  

<dict>

  <key>PayloadType</key>

  <string>Configuration</string>

  <key>PayloadVersion</key>

  <integer>1</integer>

  <key>PayloadIdentifier</key>

  <string>com.arcOS.faceID.lockaccess</string>

  <key>PayloadUUID</key>

  <string>"$uuid"$</string>

  <key>PayloadDisplayName</key>

  <string>Lock Screen Access Restrictions</string>

  <key>PayloadOrganization</key>

  <string>arcOS</string>

  <key>PayloadContent</key>

  <array>

    <dict>

      <key>PayloadType</key>

      <string>com.apple.applicationaccess</string>

      <key>PayloadVersion</key>

      <integer>1</integer>

      <key>PayloadIdentifier</key>

      <string>com.arcOS.faceID.lockaccess.restrictions</string>

      <key>PayloadUUID</key>

      <string>"$uuid"</string>

      <key>PayloadDisplayName</key>

      <string>Restrictions</string>

  

      <!-- Disable Control Center on lock screen -->

      <key>allowControlCenterInLockScreen</key>

      <false/>

  

      <!-- Disable Notification Center on lock screen -->

      <key>allowNotificationCenterInLockScreen</key>

      <false/>

  

      <!-- Disable Today View and Search on lock screen -->

      <key>allowTodayViewInLockScreen</key>

      <false/>

  

      <!-- Example: require passcode for USB accessories when locked -->

      <!-- (the inverse of the “USB Accessories” toggle) -->

      <key>allowUSBRestrictedMode</key>

      <true/>

    </dict>

<!--- airdrop discovery --->

<dict>

  <key>PayloadContent</key>

  <array>

    <dict>

      <key>PayloadType</key>

      <string>com.apple.sharingd</string>

      <key>PayloadVersion</key>

      <integer>1</integer>

      <key>PayloadIdentifier</key>

      <string>com.arcOS.nearby.profile.sharingd</string>

      <key>PayloadUUID</key>

      <string>$uuid</string>

      <key>PayloadDisplayName</key>

      <string>AirDrop</string>

  

      <!-- macOS only: AirDrop discoverability -->

      <key>DiscoverableMode</key>

      <string>Everyone</string>

      <!-- Allowed values on macOS: Everyone, Contacts Only, Off -->

    </dict>

  </array>

  

  <key>PayloadType</key>

  <string>Configuration</string>

  <key>PayloadVersion</key>

  <integer>1</integer>

  <key>PayloadIdentifier</key>

  <string>com.arcOS.nearby.profile</string>

  <key>PayloadUUID</key>

  <string>$uuid</string>

  <key>PayloadDisplayName</key>

  <string>AirDrop Discoverability</string>

</dict>

  

    <~--disconnect secureenclave-->

<dict>

  <key>PayloadContent</key>

  <array>

    <dict>

      <key>PayloadType</key>

      <string>com.apple.mobiledevice.passwordpolicy</string>

      <key>PayloadVersion</key>

      <integer>1</integer>

      <key>PayloadIdentifier</key>

      <string>com.arcOS.passcode</string>

      <key>PayloadUUID</key>

      <string>${PROFILE_UUID}</string>

      <key>PayloadDisplayName</key>

      <string>Passcode Policy</string>

      <key>minLength</key>

      <integer>6</integer>

      <key>maxFailedAttempts</key>

      <integer>10</integer>

      <key>requireAlphanumeric</key>

      <false/>

    </dict>

  </array>

  <key>PayloadType</key>

  <string>Configuration</string>

  <key>PayloadVersion</key>

  <integer>1</integer>

  <key>PayloadIdentifier</key>

  <string>com.arcOS.root</string>

  <key>PayloadUUID</key>

  <string>"$uuid"</string>

  <key>PayloadDisplayName</key>

  <string>${ORG} Security Policy</string>

</dict>

  

<!--- mdm enrollment, servercapabilities --->

<dict>

  <key>PayloadType</key>

  <string>Configuration</string>

  <key>PayloadVersion</key>

  <integer>1</integer>

  <key>PayloadIdentifier</key>

  <string>com.arcOS.mdm.enroll</string>

  <key>PayloadUUID</key>

  <string>"$uuid"</string>

  <key>PayloadDisplayName</key>

  <string>MDM Enrollment</string>

  

  <key>PayloadContent</key>

  <array>

    <dict>

      <key>PayloadType</key>

      <string>com.arcOS.mdm</string>

      <key>PayloadVersion</key>

      <integer>1</integer>

      <key>PayloadIdentifier</key>

      <string>com.arcOS.mdm.enroll.mdm</string>

      <key>PayloadUUID</key>

      <string>"$uuid"</string>

      <key>PayloadDisplayName</key>

      <string>MDM</string>

  

      <key>ServerURL</key>

      <string>https://mdm.example.com/mdm</string>

      <key>CheckInURL</key>

      <string>https://mdm.example.com/checkin</string>

      <key>Topic</key>

      <string>com.apple.mgmt.External.your-topic</string>

  

      <key>ServerCapabilities</key>

      <array>

        <string>$MDM_CONFIG_NAME</string>

      </array>

    </dict>

  </array>

</dict>

</plist>

EOF

  

  

  

#### Sign the mobileconfig (self-signed for testing)

  

# Read the MDM configuration dictionary

mdm_config=$(defaults read com.apple.configuration.managed 2>/dev/null)

YOURSETTINGKEY="*"

  

# Check if MDM config exists

if [ -n "$mdm_config" ]; then

    echo "MDM Configuration found"

    # Read a specific key from the managed configuration

    server_url=$(defaults read com.apple.configuration.managed $YOURSETTINGKEY 2>/dev/null)

    installMDM 

    if [ -n "$server_url" ]; then

        echo "Server URL: $server_url"

        defaults read com.apple.configuration.managed 2>/dev/null)     

        # Use the configuration value

    else

        echo "yourSettingKey not found in MDM config"

        installMDM 

    fi

else

    echo "No MDM configuration found"

    installMDM 

fi

  

  

installMDM(){

security cms -S -N -n "arcOS Security" -i "$MDM_CONFIG_NAME.$MDM_FILE_FORMAT -o $MDM_NAME"

  

echo "Files created:" 

echo "$MDM_CONFIG_NAME.$MDM_FILE_FORMAT - Xcode build xcconfig entitlements mobileconfig" 

echo "Install: Open $MDM_NAME.$MDM_FILE_FORMAT in arcOS + AppleOS Settings" 

  

  

#### Auto-notification + exit

echo "arcOS MDM is deployed on your system"

  

  

CONFIG_PATH="$MDM_CONFIG_NAME.$MDM.FILE_FORMAT"  # From Xcode export

  

####Install profile

sudo profiles install -path="$CONFIG_PATH"

plutil -lint "$MDM_CONFIG_NAME.$MDM_FILE_FORMAT"

&

  

}

  

installMDM 

# Example: write to arcOS plist via defaults

#/usr/bin/defaults write com.arcos ProfileName -string "$MDM_CONFIG_NAME"

#/usr/bin/defaults write com.arcos SomeBooleanOption -bool true

#/usr/bin/defaults write com.example.arcos SomeIntegerValue -int 1

  

}

  

  

  

  

randomizeIconQQshell(){

  

  

OUT="${1:-random-homescreen.mobileconfig}"

DEVICE_NAME="${DEVICE_NAME:-arcOS_QQDEVICE}"

ORG="${ORG:-arcOS}"

UUID_MAIN=""$uuid""

#UUID_WC1=""$uuid""

#UUID_WC2=""$uuid""

#UUID_HSL=""$uuid""

  

# Edit these

#LABELS=("Portal" "Helpdesk")

#URLS=("https://portal.example.com" "https://help.example.com")

  

# Shuffle indexes

idx=(0 1)

shuf_idx=($(printf "%s\n" "${idx[@]}" | shuf))

  

URL_A="${URLS[${shuf_idx[0]}]}"

URL_B="${URLS[${shuf_idx[1]}]}"

LABEL_A="${LABELS[${shuf_idx[0]}]}"

LABEL_B="${LABELS[${shuf_idx[1]}]}"

  

cat > "$arcOS_ios_appIcon" <<EOF

<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">

<plist version="1.0">

<dict>

  <key>PayloadType</key><string>Configuration</string>

  <key>PayloadVersion</key><integer>1</integer>

  <key>PayloadIdentifier</key><string>com.arcOS.randomhomescreen</string>

  <key>PayloadUUID</key><string>${UUID_MAIN}</string>

  <key>PayloadDisplayName</key><string>${DEVICE_NAME}</string>

  <key>PayloadOrganization</key><string>${ORG}</string>

  <key>PayloadContent</key>

  <array>

  

    <dict>

      <key>PayloadType</key><string>com.apple.webClip.managed</string>

      <key>PayloadVersion</key><integer>1</integer>

      <key>PayloadIdentifier</key><string>com.example.webclip.*</string>

      <key>PayloadUUID</key><string>${UUID_APPCLIP}</string>

      <key>PayloadDisplayName</key><string>${LABEL_A}</string>

      <key>Label</key><string>${LABEL_A}</string>

      <key>URL</key><string>${URL_A}</string>

      <key>IsRemovable</key><false/>

      <key>FullScreen</key><true/>

      <key>Precomposed</key><true/>

    </dict>

  

  </array>

</dict>

</plist>

EOF

  

  

}

  

  

  

  

resetmdmQQshell=$arcOSSyntaxKit[0]

  

BUNDLE_ID="$1"

APP_STORE_ID="$2"

APP_NAME="$3"

  

OUT_DIR="${PWD}/mdm-output"

mkdir -p "$OUT_DIR"

  

PROFILE_UUID="$(uuidgen | tr '[:upper:]' '[:lower:]')"

PAYLOAD_UUID="$(uuidgen | tr '[:upper:]' '[:lower:]')"

ORG="Example Org"

  

cat > "${OUT_DIR}/required-app-profile.mobileconfig" <<EOF

<?xml version="1.0" encoding="UTF-8"?>

<!DOCTYPE plist PUBLIC "-//Apple//DTD PLIST 1.0//EN" "http://www.apple.com/DTDs/PropertyList-1.0.dtd">

<plist version="1.0">

<dict>

<key>PayloadContent</key>

<array>

<dict>

<key>PayloadType</key>

<string>com.apple.mdm</string>

<key>PayloadVersion</key>

<integer>1</integer>

<key>PayloadIdentifier</key>

<string>${ORG}.mdm.required-app</string>

<key>PayloadUUID</key>

<string>${PAYLOAD_UUID}</string>

<key>PayloadDisplayName</key>

<string>${APP_NAME} Required App Enrollment</string>

  

<!-- Replace these with your actual MDM enrollment values -->

<key>ServerURL</key>

<string>https://mdm.example.com/checkin</string>

<key>CheckInURL</key>

<string>https://mdm.example.com/checkin</string>

<key>Topic</key>

<string>com.apple.mgmt.External.YOUR_TOPIC_HERE</string>

<key>SignMessage</key>

<true/>

<key>AccessRights</key>

<integer>8191</integer>

  

<!-- Keep these as metadata for your workflow -->

<key>RequiredAppBundleID</key>

<string>${BUNDLE_ID}</string>

<key>RequiredAppStoreID</key>

<string>${APP_STORE_ID}</string>

<key>RequiredAppName</key>

<string>${APP_NAME}</string>

</dict>

</array>

  

<key>PayloadDisplayName</key>

<string>${APP_NAME} Enrollment Profile</string>

<key>PayloadIdentifier</key>

<string>${ORG}.enrollment.${BUNDLE_ID}</string>

<key>PayloadRemovalDisallowed</key>

<false/>

<key>PayloadType</key>

<string>Configuration</string>

<key>PayloadUUID</key>

<string>${PROFILE_UUID}</string>

<key>PayloadVersion</key>

<integer>1</integer>

<key>PayloadOrganization</key>

<string>${ORG}</string>

</dict>

</plist>

EOF

  

cat > "${OUT_DIR}/install-application-command.json" <<EOF

{

"RequestType": "InstallApplication",

"iTunesStoreID": ${APP_STORE_ID},

"ManagementFlags": 1,

"Attributes": {

"Removable": false

 },

"ChangeManagementState": "Managed"

}

EOF

  

cat > "${OUT_DIR}/README.txt" <<EOF

App Name: ${APP_NAME}

Bundle ID: ${BUNDLE_ID}

App Store ID: ${APP_STORE_ID}

  

Notes:

- On unsupervised devices, Apple supports one Required App flow during MDM enrollment.

- For third-party App Store apps, InstallApplication typically uses the App Store ID.

- Blocklist/allowlist by bundle ID requires supervised devices.

- Replace the sample MDM URLs, topic, and command fields to match your MDM server.

EOF

  

echo "Created:"

echo "  ${OUT_DIR}/required-app-profile.mobileconfig"

echo "  ${OUT_DIR}/install-application-command.json"

echo "  ${OUT_DIR}/README.txt"

  

&

  

  

  

  

exit 0 & 

$arcOSSyntaxKit[1]

  

  

# 66666666-7777-8888-9999-AAAAAAAAAAAA 

# 11111111-2222-3333-4444-555555555555

# 4A919E36-912E-41C4-AD9D-DC11A15C272B

  

#!/bin/bash

  

buildBluePrint_IOS=$arcOSSyntaxKit[0]

  

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

  

  

$arcOSSyntaxKit[1]
```