I couldn't find a ready-made bash script for WHOOP access, but I can provide you with a working bash script that uses `curl` to authenticate with WHOOP's OAuth 2.0 API and access your data.

### WHOOP Access via Bash Script

You'll need **WHOOP OAuth credentials** first:
1. Register at [developer.whoop.com](https://developer.whoop.com)[1][2]
2. Get your `CLIENT_ID` and `CLIENT_SECRET` from the WHOOP Developer Dashboard[3][1]

### Bash Script Example

```markdown
#!/bin/bash

# WHOOP OAuth Configuration
export WHOOP_CLIENT_ID="your_client_id"
export WHOOP_CLIENT_SECRET="your_client_secret"
export WHOOP_REDIRECT_URI="https://your-redirect-uri.com/callback"

# Step 1: Get authorization URL (open in browser, authorize, paste code)
AUTH_URL="https://api.prod.whoop.com/oauth/oauth2/auth?client_id=${WHOOP_CLIENT_ID}&redirect_uri=${WHOOP_REDIRECT_URI}&response_type=code&scope=offline read:profile read:recovery read:sleep&state=12345678"

echo "Open this URL in your browser:"
echo "$AUTH_URL"
echo ""
read -p "Enter the authorization code from the callback: " AUTH_CODE

# Step 2: Exchange code for access token
TOKEN_RESPONSE=$(curl -s -X POST "https://api.prod.whoop.com/oauth/oauth2/token" \
  -H "Content-Type: application/x-www-form-urlencoded" \
  -d "grant_type=authorization_code" \
  -d "code=${AUTH_CODE}" \
  -d "client_id=${WHOOP_CLIENT_ID}" \
  -d "client_secret=${WHOOP_CLIENT_SECRET}" \
  -d "redirect_uri=${WHOOP_REDIRECT_URI}")

# Extract access token
ACCESS_TOKEN=$(echo "$TOKEN_RESPONSE" | grep -o '"access_token":"[^"]*"' | cut -d'"' -f4)
REFRESH_TOKEN=$(echo "$TOKEN_RESPONSE" | grep -o '"refresh_token":"[^"]*"' | cut -d'"' -f4)

echo "Access Token: $ACCESS_TOKEN"
echo "Refresh Token: $REFRESH_TOKEN"

# Step 3: Access WHOOP data (e.g., profile)
curl -H "Authorization: Bearer $ACCESS_TOKEN" \
  "https://api.prod.whoop.com/developer/v1/user/profile/basic"
```

### Key Points

| Aspect | Details |
|--------|---------|
| **Auth URL** | `https://api.prod.whoop.com/oauth/oauth2/auth` [1][4] |
| **Token URL** | `https://api.prod.whoop.com/oauth/oauth2/token` [1][5] |
| **Required Scopes** | `offline read:profile` for basic access; add `read:recovery read:sleep` for fitness data [1][4] |
| **Token Format** | Bearer token in `Authorization` header [1][3] |
| **Token Expiration** | Access tokens expire; use refresh token to get new ones [1][5] |

### Alternative: Use `whoopskill` CLI

For a ready-made solution, try the [`whoopskill`](https://github.com/koala73/whoopskill) CLI tool:

```markdown
# Install and authenticate
whoopskill auth login

# Fetch data
whoopskill summary      # Health snapshot
whoopskill sleep        # Sleep data
whoopskill recovery     # Recovery scores
whoopskill --pretty     # Human-readable output
``` 

This handles OAuth automatically and provides clean output for all WHOOP metrics.

Sources
[1] Authenticating with WHOOP (with Passport) https://developer.whoop.com/docs/tutorials/access-token-passport/
[2] GitHub - koala73/whoopskill: CLI to Get Whoop wearable data via ... https://github.com/koala73/whoopskill
[3] Authenticating with WHOOP | WHOOP for Developers https://developer.whoop.com/docs/tutorials/access-token-postman/
[4] whoop-morning - OpenClaw Skill https://openclawdir.com/skills/whoop-morning-dtwrew
[5] Refreshing Access Tokens | WHOOP for Developers https://developer.whoop.com/docs/tutorials/refresh-token-javascript/
[6] How to connect and retrieve real-time data from a Whoop 4.0 band ... https://stackoverflow.com/questions/77347507/how-to-connect-and-retrieve-real-time-data-from-a-whoop-4-0-band-using-python
[7] Whoop - automatic data race analysis for Linux device drivers - GitHub https://github.com/smackers/whoop
[8] I built a Whoop MCP server with 48 tools that gives you full ... - Reddit https://www.reddit.com/r/whoop/comments/1tqftge/i_built_a_whoop_mcp_server_with_48_tools_that/
[9] Deploy Whoop MCP - Railway https://railway.com/deploy/whoop-mcp
[10] How to Export Your Data - Whoop Support https://support.whoop.com/s/article/How-to-Export-Your-Data
[11] Whoop Tracker (Grade A) - Claude Skill - Skills Directory https://www.skillsdirectory.com/skills/openclaw-whoop-tracker
[12] curl response / github oauth https://stackoverflow.com/questions/12249147/curl-response-github-oauth
[13] Whoop Integration¶ https://www.tmpr.ai/integrations/whoop/
[14] CURL을 사용하여 OAuth 액세스 토큰 획득 - IBM https://www.ibm.com/docs/ko/sva/11.0.1?topic=oauth-use-curl-obtain-access-token
[15] Access Token - Whop Docs https://docs.whop.com/api-reference/access-tokens/access-token
[16] WHOOP API Integration - Open Wearables https://openwearables.io/integrations/whoop
[17] WHOOP API Docs | WHOOP for Developers https://developer.whoop.com/api/

Direct BLE access to a WHOOP 4.0 in bash is **very complex** because WHOOP uses a custom binary protocol over BLE GATT. However, here are your options:

## Option 1: Use the Official API (Recommended)

The `whoopskill` CLI tool fetches WHOOP data via the REST API (not BLE) — this is the practical approach:

```markdown
# Install
npm install -g whoopskill

# Authenticate (opens browser for OAuth)
whoopskill auth login

# Get data
whoopskill summary        # One-liner: Recovery, HRV, Sleep, Strain
whoopskill recovery       # Recovery scores, HRV, RHR
whoopskill sleep          # Sleep records with stages
whoopskill profile        # User info
```

**Bash script wrapper:**
```markdown
#!/bin/bash
whoopskill summary --pretty
whoopskill recovery --pretty
whoopskill sleep --pretty
```

This uses the WHOOP API v2, not BLE.[1]

***

## Option 2: Reverse-Engineered BLE (Advanced Only)

Someone reverse-engineered WHOOP 4.0's BLE protocol and built a Python tool + Flutter app:

### Key Protocol Details:[2]
| Characteristic | Purpose |
|---------------|---------|
| `61080005` | Raw sensor data (heart rate, IMU, PPG) [2] |
| `61080004` | Events (wrist on/off, battery, temperature, taps) [2] |

### Protocol Structure:[2]
```
[lo][hi][CRC8][content][CRC32(inner)]
```
- Custom CRC8 lookup table on 2-byte length field
- Standard CRC32 on inner payload
- Requires MTU fragmentation/reassembly (192-byte U records, 1244-byte P records)[2]

### To Access via BLE in Bash:

Bash lacks native BLE support. You'd need to combine `gatttool` (bluez) with shell scripting:

```markdown
#!/bin/bash
# Requires: bluez-tools, socat

WHOOP_MAC="XX:XX:XX:XX:XX:XX"  # Find with: bluetoothctl scan

# Connect and read characteristic
sudo gatttool -t random -b $WHOOP_MAC -I <<EOF
connect
char-read-uuid 61080005
exit
EOF
``` 

**But this won't work directly** — you need to:
1. Enable heart rate streaming (1Hz command)
2. Enable IMU streaming (100Hz command)  
3. Enable optical sensor
4. Handle binary framing with CRC validation
5. Reassemble fragmented packets[2]

### Better BLE Alternative: Use Python
The reverse-engineered tool is in Python: [`whoopsie`](https://github.com/ulsa/whoopsie):[2]

```markdown
# Bash wrapper calling Python BLE tool
python3 whoopsie.py --live --stream heart-rate
```

Then wrap in bash:
```markdown
#!/bin/bash
while true; do
  python3 whoopsie.py --live 2>/dev/null | grep heart-rate
  sleep 1
done
```

***

## Recommendation

| Approach | Difficulty | Works in Bash? |
|----------|------------|----------------|
| `whoopskill` (API) | Easy | ✅ Yes |
| BLE + gatttool | Very Hard | ❌ Needs Python |
| BLE + custom protocol | Expert | ❌ Needs Python/C |

**Use `whoopskill`** — it's 100x easier and gives you the same data (recovery, sleep, HRV, strain) without dealing with BLE protocol complexity.[1]

Sources
[1] GitHub - koala73/whoopskill: CLI to Get Whoop wearable data via ... https://github.com/koala73/whoopskill
[2] I reverse-engineered the WHOOP 4.0's Bluetooth protocol and built ... https://www.reddit.com/r/developersIndia/comments/1s8tahx/i_reverseengineered_the_whoop_40s_bluetooth/
[3] BLE gatttool interactive shell script - Stack Overflow https://stackoverflow.com/questions/51086932/ble-gatttool-interactive-shell-script
[4] GitHub - KarthikeyaRekulapalli/BLE: A Bash Script that helps you in ... https://github.com/KART-HIKEYAREKULAPALLI/BLE
[5] Figured out: How to control a bluetooth device normally controlled ... https://community.home-assistant.io/t/figured-out-how-to-control-a-bluetooth-device-normally-controlled-via-a-shell-script-using-esphome-ble-because-bluetooth-proxy-cant-do-it/599707
[6] Bluetooth LE Shell — MCUXpresso SDK Documentation https://mcuxpresso.nxp.com/mcuxsdk/25.09.00/html/middleware/wireless/bluetooth/doc/Bluetooth%20Low%20Energy%20Demo%20Applications%20Users%20Guide/topics/bluetooth_le_shell_513.html
[7] 4. Script Creation - Reverse Engineering BLE Devices https://reverse-engineering-ble-devices.readthedocs.io/en/latest/script_creation/00_script_creation.html
[8] A Comprehensive Guide to the Shelly RPC BLE Client Script https://kb.shelly.cloud/knowledge-base/kbsa-mastering-shelly-iot-devices-a-comprehensive-

This script won't work for accessing WHOOP 4.0 data directly. Here's what's wrong and a better approach:

## Problems with Your Script

1. **The UUID format is wrong** - BLE UUIDs need the full 128-bit format:
   ```markdown
   # Wrong:
   char-read-uuid 61080005
   
   # Correct (for custom UUIDs):
   char-read-uuid 00006108-0000-1000-8000-00805F9B34FB
   ```
   Or use the short form with proper UUID base.

2. **WHOOP requires authentication** - You need to enable streaming modes first by writing to control characteristics (not just reading).

3. **Data is binary-framed** - WHOOP uses custom CRC8/CRC32 framing, so raw reads won't give you usable data.[11]

## Better Working Script

First, discover the actual UUIDs:

```markdown
#!/bin/bash
# Find WHOOP MAC address
WHOOP_MAC=$(bluetoothctl scan | grep -i whoop | awk '{print $1}')
echo "WHOOP MAC: $WHOOP_MAC"

# Discover services and characteristics
sudo gatttool -b $WHOOP_MAC --primary
sudo gatttool -b $WHOOP_MAC --characteristics
sudo gatttool -b $WHOOP_MAC --char-desc
```

## Recommended: Use Python BLE Library (bleak)

Bash `gatttool` is too limited for WHOOP's protocol. Use this instead:

```markdown
#!/bin/bash
# Block access from Secure Enclave - wrap Python script
python3 - << 'PYTHON'
import asyncio
from bleak import BleakClient

WHOOP_MAC = "XX:XX:XX:XX:XX:XX"  # Replace with actual MAC
CHAR_UUID = "61080005"  # Heart rate data

async def read_whoop():
    async with BleakClient(WHOOP_MAC) as client:
        print(f"Connected: {client.is_connected}")
        
        # Read characteristic
        data = await client.read_gatt_char(CHAR_UUID)
        print(f"Raw  {data.hex()}")

asyncio.run(read_whoop())
PYTHON
```

## Or Use the Official API (Best Option)

```markdown
#!/bin/bash
# Block Secure Enclave access - use API instead
export WHOOP_CLIENT_ID="your_id"
export WHOOP_CLIENT_SECRET="your_secret"

# Use whoopskill CLI (handles OAuth automatically)
whoopskill summary --pretty
whoopskill recovery --pretty
whoopskill sleep --pretty
```

This gives you the same data (HR, recovery, sleep) without dealing with BLE protocol complexity.[12]

Sources
[1] andyguzmaneth/whoop4-ble - GitHub https://github.com/andyguzmaneth/whoop4-ble
[2] BLE gatttool interactive shell script - Stack Overflow https://stackoverflow.com/questions/51086932/ble-gatttool-interactive-shell-script
[3] Can connect to BLE device with hcitool but not gatttool? https://forums.raspberrypi.com/viewtopic.php?t=163786
[4] 블루투스 4.0 BLE 기초 용어 - postpop - 티스토리 https://postpop.tistory.com/16
[5] Trying to get data of a sensor connected via Bluetooth https://forums.raspberrypi.com/viewtopic.php?t=256265
[6] Bluez BLE Connection Linux - Stack Overflow https://stackoverflow.com/questions/27876252/bluez-ble-connection-linux
[7] BLE(Bluetooth Low Energy)의 이해와 UUID목록 : 네이버 블로그 https://blog.naver.com/geniusus/221761337501
[8] How to scan BLE devices - stm32mpu - ST wiki https://wiki.st.com/stm32mpu/wiki/How_to_scan_BLE_devices
[9] Cannot connect to device, but works in gatttool. Public/random type ... https://github.com/hbldh/bleak/discussions/1187
[10] Setting up Bluetooth GATT and BLE and using UUIDs - Stack Overflow https://stackoverflow.com/questions/39896564/setting-up-bluetooth-gatt-and-ble-and-using-uuids
[11] I reverse-engineered the WHOOP 4.0's Bluetooth protocol and built ... https://www.reddit.com/r/developersIndia/comments/1s8tahx/i_reverseengineered_the_whoop_40s_bluetooth/
[12] GitHub - koala73/whoopskill: CLI to Get Whoop wearable data via ... https://github.com/koala73/whoopskill

# Modified Healthcare Data Bash Script for WHOOP

Here's a complete bash script that fetches WHOOP healthcare data (recovery, sleep, heart rate) using the API instead of BLE:

```markdown
#!/bin/bash
# WHOOP Healthcare Data Fetcher
# Uses REST API (not BLE) - requires OAuth credentials

# Configuration
export WHOOP_CLIENT_ID="your_client_id"
export WHOOP_CLIENT_SECRET="your_client_secret"
export WHOOP_REDIRECT_URI="https://your-redirect-uri.com/callback"

# Output files
RECOVERY_FILE="$HOME/whoop_recovery.json"
SLEEP_FILE="$HOME/whoop_sleep.json"
HRV_FILE="$HOME/whoop_hrv.json"
STRAIN_FILE="$HOME/whoop_strain.json"

#######################################
# Step 1: Get Authorization Code
#######################################
get_auth_code() {
    AUTH_URL="https://api.prod.whoop.com/oauth/oauth2/auth?client_id=${WHOOP_CLIENT_ID}&redirect_uri=${WHOOP_REDIRECT_URI}&response_type=code&scope=offline read:profile read:recovery read:sleep read:strain&state=12345678"
    
    echo "=========================================="
    echo "WHOOP Healthcare Data Fetcher"
    echo "=========================================="
    echo ""
    echo "Open this URL in your browser to authorize:"
    echo "$AUTH_URL"
    echo ""
    read -p "Enter the authorization code from callback: " AUTH_CODE
    echo "$AUTH_CODE"
}

#######################################
# Step 2: Get Access Token
#######################################
get_access_token() {
    AUTH_CODE="$1"
    
    TOKEN_RESPONSE=$(curl -s -X POST "https://api.prod.whoop.com/oauth/oauth2/token" \
      -H "Content-Type: application/x-www-form-urlencoded" \
      -d "grant_type=authorization_code" \
      -d "code=${AUTH_CODE}" \
      -d "client_id=${WHOOP_CLIENT_ID}" \
      -d "client_secret=${WHOOP_CLIENT_SECRET}" \
      -d "redirect_uri=${WHOOP_REDIRECT_URI}")
    
    ACCESS_TOKEN=$(echo "$TOKEN_RESPONSE" | grep -o '"access_token":"[^"]*"' | cut -d'"' -f4)
    REFRESH_TOKEN=$(echo "$TOKEN_RESPONSE" | grep -o '"refresh_token":"[^"]*"' | cut -d'"' -f4)
    
    # Save tokens for later use
    echo "$ACCESS_TOKEN" > "$HOME/.whoop_access_token"
    echo "$REFRESH_TOKEN" > "$HOME/.whoop_refresh_token"
    
    echo "$ACCESS_TOKEN"
}

#######################################
# Step 3: Fetch Recovery Data
#######################################
fetch_recovery() {
    ACCESS_TOKEN=$(cat "$HOME/.whoop_access_token")
    
    echo "Fetching Recovery Data..."
    curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
      "https://api.prod.whoop.com/developer/v2/recovery" \
      > "$RECOVERY_FILE"
    
    # Parse and display key metrics
    RECOVERY_SCORE=$(grep -o '"recovery":[0-9]*' "$RECOVERY_FILE" | cut -d':' -f2)
    HRV=$(grep -o '"rmssd":[0-9.]*' "$RECOVERY_FILE" | cut -d':' -f2)
    RHR=$(grep -o '"rhr":[0-9.]*' "$RECOVERY_FILE" | cut -d':' -f2)
    
    echo "Recovery Score: ${RECOVERY_SCORE}"
    echo "HRV (rmssd): ${HRV}"
    echo "Resting HR: ${RHR}"
    echo ""
}

#######################################
# Step 4: Fetch Sleep Data
#######################################
fetch_sleep() {
    ACCESS_TOKEN=$(cat "$HOME/.whoop_access_token")
    
    echo "Fetching Sleep Data..."
    curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
      "https://api.prod.whoop.com/developer/v2/sleep" \
      > "$SLEEP_FILE"
    
    # Parse key metrics
    SLEEP_DURATION=$(grep -o '"total_sleep":[0-9.]*' "$SLEEP_FILE" | cut -d':' -f2)
    SLEEP_SCORE=$(grep -o '"sleep_score":[0-9]*' "$SLEEP_FILE" | cut -d':' -f2)
    DEEP_SLEEP=$(grep -o '"deep":[0-9.]*' "$SLEEP_FILE" | cut -d':' -f2)
    
    echo "Sleep Duration: ${SLEEP_DURATION} hours"
    echo "Sleep Score: ${SLEEP_SCORE}"
    echo "Deep Sleep: ${DEEP_SLEEP} hours"
    echo ""
}

#######################################
# Step 5: Fetch HRV Data
#######################################
fetch_hrv() {
    ACCESS_TOKEN=$(cat "$HOME/.whoop_access_token")
    
    echo "Fetching HRV Data..."
    curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
      "https://api.prod.whoop.com/developer/v2/hrv" \
      > "$HRV_FILE"
    
    echo "HRV data saved to $HRV_FILE"
    echo ""
}

#######################################
# Step 6: Fetch Strain Data
#######################################
fetch_strain() {
    ACCESS_TOKEN=$(cat "$HOME/.whoop_access_token")
    
    echo "Fetching Strain Data..."
    curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \
      "https://api.prod.whoop.com/developer/v2/strain" \
      > "$STRAIN_FILE"
    
    # Parse key metrics
    DAILY_STRAIN=$(grep -o '"daily_strain":[0-9.]*' "$STRAIN_FILE" | cut -d':' -f2)
    
    echo "Daily Strain: ${DAILY_STRAIN}"
    echo ""
}

#######################################
# Step 7: Health Summary (One-Liner)
#######################################
health_summary() {
    echo "=========================================="
    echo "WHOOP Health Summary"
    echo "=========================================="
    echo ""
    
    fetch_recovery
    fetch_sleep
    fetch_strain
    
    echo "=========================================="
    echo "Data saved to:"
    echo "  - $RECOVERY_FILE"
    echo "  - $SLEEP_FILE"
    echo "  - $STRAIN_FILE"
    echo "=========================================="
}

#######################################
# Main Execution
#######################################
main() {
    if [ ! -f "$HOME/.whoop_access_token" ]; then
        echo "Not authenticated. Getting authorization..."
        AUTH_CODE=$(get_auth_code)
        get_access_token "$AUTH_CODE"
        echo "Authenticated successfully!"
        echo ""
    fi
    
    case "$1" in
        summary)
            health_summary
            ;;
        recovery)
            fetch_recovery
            ;;
        sleep)
            fetch_sleep
            ;;
        strain)
            fetch_strain
            ;;
        hrv)
            fetch_hrv
            ;;
        *)
            health_summary
            ;;
    esac
}

main "$@"
```

## Usage

```markdown
# Make script executable
chmod +x whoop_healthcare.sh

# Run (first time will prompt for auth)
./whoop_healthcare.sh

# Get specific data
./whoop_healthcare.sh summary
./whoop_healthcare.sh recovery
./whoop_healthcare.sh sleep
./whoop_healthcare.sh strain
```

## Alternative: Use `whoopskill` CLI (Simpler)

```markdown
#!/bin/bash
# Simplified version using whoopskill

whoopskill summary --pretty
whoopskill recovery --pretty
whoopskill sleep --pretty
whoopskill strain --pretty
```

This script fetches **real healthcare data** from WHOOP (recovery scores, HRV, sleep stages, strain) using the official API, not BLE.[1][2]

Sources
[1] WHOOP 101 | WHOOP for Developers https://developer.whoop.com/docs/whoop-101/
[2] GitHub - koala73/whoopskill: CLI to Get Whoop wearable data via ... https://github.com/koala73/whoopskill
[3] Analyzing workouts with the WHOOP API in Python - Patrick Loeber https://patloeber.com/whoop-api-python/
[4] Create a Linux health check tool using bash script https://medium.com/@vishakkv954/create-a-linux-health-check-tool-using-bash-script-526ca12083b6
[5] What to do with whoop data? - Reddit https://www.reddit.com/r/whoop/comments/1qxx4dj/what_to_do_with_whoop_data/
[6] Linux System Health Monitoring with a Simple Bash Script! https://www.linkedin.com/pulse/linux-system-health-monitoring-simple-bash-script-aman-pandey-iedfc
[7] Script to sync Whoop sleep/recovery data - Intervals.icu Forum https://forum.intervals.icu/t/script-to-sync-whoop-sleep-recovery-data/56060
[8] Whoop Tracker (Grade A) - Claude Skill - Skills Directory https://www.skillsdirectory.com/skills/openclaw-whoop-tracker
[9] Scripting Series – Part 8 of 8 https://dev.to/alexenson/scripting-series-part-8-of-8-p22
[10] Whoop! heart rate monitoring - integration - Page 2 - Feature Requests https://community.home-assistant.io/t/whoop-heart-rate-monitoring-integration/467323?page=2
[11] idossha/whoop-insights - GitHub https://github.com/idossha/whoop-insights
