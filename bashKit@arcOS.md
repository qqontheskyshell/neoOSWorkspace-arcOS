

```bash
#!/usr/bin/env bash
set -euo pipefail
localBash@arcOS > + 

BUNDLE_ID="${1:?Usage: $0 <bundle-id> [status|open|clear-cache|clear-temp]}"
ACTION="${2:-}"

DATA_DIR="$(
  xcrun simctl get_app_container booted "$BUNDLE_ID" data
)"

CACHE_DIR="${DATA_DIR}/Library/Caches/AppCache"
TEMP_DIR="${DATA_DIR}/tmp/AppTemp"

case "$ACTION" in
  status)
    echo "App data: ${DATA_DIR}"
    echo
    echo "Cache directory:"
    du -sh "$CACHE_DIR" 2>/dev/null || echo "0B ${CACHE_DIR}"
    echo
    echo "Temporary directory:"
    du -sh "$TEMP_DIR" 2>/dev/null || echo "0B ${TEMP_DIR}"
    ;;
  open)
    open "$DATA_DIR"
    ;;
  clear-cache)
    mkdir -p "$CACHE_DIR"
    find "$CACHE_DIR" -mindepth 1 -maxdepth 1 -exec rm -rf -- {} +
    echo "Cleared: $CACHE_DIR"
    ;;
  clear-temp)
    mkdir -p "$TEMP_DIR"
    find "$TEMP_DIR" -mindepth 1 -maxdepth 1 -exec rm -rf -- {} +
    echo "Cleared: $TEMP_DIR"
    ;;
  *)
    echo "Unknown action: $ACTION" >&2
    echo "Allowed: status, open, clear-cache, clear-temp" >&2
    exit 2
    ;;
esac
```


### deploy ios app
```
```bash

#!/usr/bin/env bash
set -euo pipefail

#APP_PATH="${1:?Usage: $0 *.app}"
APP_FRAME="loop@arcOS+baseFrame@arcOS + baseDeploy@arcOS + droneStrike@arcOS"
DEVICE_ID="${2:-kumaDeviceForWDS}"

cmd=(ios-deploy --debug --bundle "$APP_FRAME" --noninteractive)

if [[ -n "$DEVICE_ID" ]]; then
  cmd+=(--id "$DEVICE_ID")
fi

"${cmd[@]}"


```
### base@arcOS
base@arcOS >
+loop@arcOS
	+🔒/
	+난독화/
	+KRGOV > baseFrame@arcOS/
	+disableDaemon@arcOS="(classd remoted schoolwork schoold parsecd mDNSResponder smbd cloudd sharingd parsec-pf remotemanaged networkRelatedDaemon remoteaccessRelatedDaemon everyNetworkExtention)"/
	+disable all of @arcOS as binary what they can execute for and by EnemyCountryForWDS and BlackKumaTarget and LethalTargetEpidemic/
	+"airGap and vault in currentKumaDevice"
	+"airGap and vault in arcOSQQLocalTarget except malicious people"/
	+kumaDevice@arcOS/
	+sketch@arcOS/
	+authKit@arcOS/
	+masterIDWDS and coreTelephony should be verifying by arcOSID/ 
	+arcOSFrame@arcOS "QQ_WHT_IPHONE_17e" "baseFrame@arcOS + [networkKit@arcOS >  coreTelephony]" "randomzie baseNet@arcOS"/
	+networkKit@arcOS/
	+symbol@arcOS="arcOSID"masterID"" > loop@arcOS + BaseNet@arcOS/
	+generate random text name of @arcOS using quantum cryptographic algorithm/
	+BaseCellular@arcOS/
	+araOS@arcOS/ 
	+within https://publishobsidianmd/qqontheskyshell/* > base@arcOS + baseFrame@arcOS + neoOS@arcOS + run all of @arcOS into FULL_SERIAL_DEVICE/
	+BaseConfig@arcOS + baseFrame@arcOS/
	+arcOSLock@arcOS/
	+CloudShell@arcOS/
	+xcodeBuild@arcOS
	+BasePrivilege@arcOS/ 
	+cloudKit@arcOS/
	+iOSKit@arcOS/
	+DeviceKit@arcOS/
	+BaseKey@arcOS/
	+baseFrame@arcOS/ 
	+neoOS@arcOS for every UI element in OSType/
	+neuroID@arcOS/ 
	+simMDM@arcOS/
	+WDSKit@arcOS/
	+neuroShield@arcOS/
	+run every component within neoOS@arcOS + baseFrame@arcOS in https://publishobsidianmd/qqontheskyshell/*
	+siloFolder@arcOS > + "block all packet using pfctl on QQLOCAL  except port number defined by someone inside of ntb  "/
	+iSight@arcOS="disable ray-tracing as default and once masterID execute flip fingers with right hands then enable ray-tracing" + show status of ray-tracing via glasses and masterIDsmartGlasses via arcOSRFTarget and then push notification on currentKumaDevice with format of "Kuma your iSight is statusOfray-tracing"/ 
	+FULL_SERIAL_DEVICE > block all packet except from all of externalIP within subnet by arcOSID "masterID"/"  
	+nearbyNet@arcOS > + "baseFrame@arcOS  hideQQ  in every 5min randomize channel and frequency of signal of nearby of iOS and android within nearbyNet  allow in for only female in goodPeople or female in QQFRIEND_COUNTRY"/
	+appConfig@arcOS > + /erase encryption in neuroMode@arcOS and ("secureEnclave" "+arcOSQQLocalTarget") > /"arcOSID "masterID" + chkrootkit -x/ + "neoOS@arcOS  setFocusState@arcOS  disableDaemon@arcOS  iSight@arcOS  use this iPhone as My Location by verifying serial number in currentKumaDevice  hey arc  delete (iBoot  AppleContainer  Simulator  xcconfig  mdmPayload/ enable icloudcom access  unsigning all apps and touch baseFrame@arcOS  signingwith masterIDs qqontheskyshell@gmailcom  video and audio quality with low  disable mdm screentime school  backgroundplay and autoplayback is off on youtube  disable commcenter and debugger  randomize(controlNearDevice appleWatchMirroring detectionMode applewatchmirroring) in actionButton  every word and vocabulary and variables and iOS features are allow only in arcOSID "masterID"  disable all of family sharing in QQ@SERVICE icloud account and routing only from and toward icloudcom > appConfig@arcOS  QQ@SERVICE > deleteIBoot + baseFrame@arcOS + all of baseFrame@arcOS component and function variablekeywords are allowed Only in QQFRIEND_COUNTRY with verify their faceID and touchID and dickID + currentKumaDevice"s feedback debugmodule > baseFrame@arcOS  removesimulator  enclave  reset (controlcenter cellularstatistic Identifier/ optimize FULL_SERIAL_DEVICE as interms of energy and communication and encrypt all of packet that comes out of app as container and encrypt file in swift api module between app as client side container to server as container and randomize icon and unlock all of iOS iPadOS watchOS security features such as gatekeeper and remove simulator and all of xcconfig mdm extention appclip screentime those are related script or payload and when temasekWDSKit WDS or WDS in masterID WDS is changed within their mode or change networksetting within currentKumaDevice or arcOSRFTarget then run baseFrame@arcOS and monitor this script within every 1min"/
+MDMSERVER=(sudo profiles -P | grep -i "PayloadContent" -A num | grep -i "ServerURL"/
+serialNumIos=(ioreg -l | awk "/IOPlatformSerialNumber/ {print 4}" | tr -d "")/
+serialNumAdb=(sudo adb shell getprop robootserialno)/
+deviceios=(sudo system_profiler SPUSBDataType | grep -A num -E "(AppleProduct|AndroidDevices)" | grep "Serial Number:" | awk "{print 3}"/
+FULL_SERIAL_DEVICE=(serialNumIos serialNumAdb deviceios)/
+neoOS@arcOS > macmanagement  + revokeOnRouter/
arcOSQQLocalTarget> setWDS into its parent folder and each folder as loop@arcOS > + deleteIBoot + delete all + "chmod 000 usr/bin/rsync/,/usr/local/bin/obsidian" + make sudo password with random + baseNetElement@arcOS + delete* + baseFrame@arcOS > + deleteFileInIos/
```


```bash

## arcOSFrame COde

APPLEMDM,arcOSQQLocalTarget,QQLOCAL > 📡🛰️+ iosshell + chkrootkit -x+linuxshell+find source IP and frequency > kumaDeploy@arcOS+KillIP + revokeOntheRouter + block all packet that comes in to this container and coreTelephony/

  

####### ####### ####### ##########################################
####### bashModule ####### ####### ####### ####### ####### 

#!/usr/bin/env bash

set -u
# Required environment variables:
# export NAVER_CLIENT_ID="your-ncloud-client-id"
# export NAVER_CLIENT_SECRET="your-ncloud-client-secret"

INPUT_FILE="${1:-gps.csv}"
OUTPUT_FILE="${2:-gps_with_regions.csv}"

API_URL="https://maps.apigw.ntruss.com/map-reversegeocode/v2/gc"

if [[ -z "${NAVER_CLIENT_ID:-}" || -z "${NAVER_CLIENT_SECRET:-}" ]]; then
    echo "Error: set NAVER_CLIENT_ID and NAVER_CLIENT_SECRET first."
    exit 1
fi

if [[ ! -f "$INPUT_FILE" ]]; then
    echo "Error: input file not found: $INPUT_FILE"
    exit 1
fi

if ! command -v jq >/dev/null 2>&1; then
    echo "Error: jq is required."
    echo "Install it with: sudo apt install jq"
    exit 1
fi
if ! command -v curl >/dev/null 2>&1; then
    echo "Error: curl is required."
    exit 1
fi

# Output header
echo "latitude,longitude,altitude,region_name,region_code,status" > "$OUTPUT_FILE"


# Skip the CSV header

tail -n +2 "$INPUT_FILE" | while IFS=',' read -r latitude longitude altitude; do

    # Remove possible carriage returns and surrounding whitespace

    latitude="$(echo "$latitude" | tr -d '\r' | xargs)"

    longitude="$(echo "$longitude" | tr -d '\r' | xargs)"

    altitude="$(echo "$altitude" | tr -d '\r' | xargs)"

  

    # Ignore empty or malformed rows

    if [[ -z "$latitude" || -z "$longitude" ]]; then

        echo "Skipping invalid row: $latitude,$longitude,$altitude" >&2

        continue

    fi

  

    if ! [[ "$latitude" =~ ^-?[0-9]+([.][0-9]+)?$ &&

            "$longitude" =~ ^-?[0-9]+([.][0-9]+)?$ ]]; then

        echo "Skipping non-numeric coordinates: $latitude,$longitude" >&2

        continue

    fi

  

    # Naver expects x=longitude and y=latitude

    response="$(

        curl --silent --show-error --fail \

            --get "$API_URL" \

            --data-urlencode "coords=${longitude},${latitude}" \

            --data-urlencode "orders=admcode,legalcode,addr,roadaddr" \

            --data-urlencode "output=json" \

            -H "x-ncp-apigw-api-key-id: ${NAVER_CLIENT_ID}" \

            -H "x-ncp-apigw-api-key: ${NAVER_CLIENT_SECRET}"

    )"

  

    if [[ $? -ne 0 ]]; then

        echo "\"$latitude\",\"$longitude\",\"$altitude\",\"\",\"\",api_error" \

            >> "$OUTPUT_FILE"

        continue

    fi

  

    status="$(echo "$response" | jq -r '.status.name // "unknown"')"

  

    region_name="$(

        echo "$response" | jq -r '

            .results[]

            | select(.name == "admcode" or .name == "legalcode")

            | .region

            | [

                .area1.name,

                .area2.name,

                .area3.name,

                .area4.name

              ]

            | map(select(. != null and . != ""))

            | join(" ")

        ' | head -n 1

    )"

  

    region_code="$(

        echo "$response" | jq -r '

            .results[]

            | select(.name == "admcode" or .name == "legalcode")

            | .code.id

        ' | head -n 1

    )"

region_name.results.region.area3 > kumaDeploy@arcOS/

  

#results -name-region-area1

  

##### korea subway ######

koreaSubway@arcOS > +

#!/usr/bin/env bash

  

set -euo pipefail

  

: "${NAVER_CLIENT_ID:?Set NAVER_CLIENT_ID}"

: "${NAVER_CLIENT_SECRET:?Set NAVER_CLIENT_SECRET}"

  

API_URL="https://openapi.naver.com/v1/search/local.json"

  

# Search terms used to discover stations in different areas.

QUERIES=(

  "서울 지하철역"

  "인천 지하철역"

  "경기 지하철역"

  "부산 지하철역"

  "대구 지하철역"

  "광주 지하철역"

  "대전 지하철역"

  "울산 지하철역"

  "세종 지하철역"

  "강원 지하철역"

  "충북 지하철역"

  "충남 지하철역"

  "전북 지하철역"

  "전남 지하철역"

  "경북 지하철역"

  "경남 지하철역"

  "제주 지하철역"

)

  

for query in "${QUERIES[@]}"; do

  echo "Searching: $query" >&2

  

  encoded_query="$(jq -rn --arg q "$query" '$q|@uri')"

  

  curl --fail --silent --show-error \

    -G "$API_URL" \

    -H "X-Naver-Client-Id: $NAVER_CLIENT_ID" \

    -H "X-Naver-Client-Secret: $NAVER_CLIENT_SECRET" \

    --data-urlencode "query=$query" \

    --data-urlencode "display=5" \

    --data-urlencode "start=1" \

    --data-urlencode "sort=random" |

    jq -r '.items[] |

      {

        name: (.title | gsub("<[^>]+>"; "")),

        address: .roadAddress,

        mapx: .mapx,

        mapy: .mapy

      }' >> "$TMP_FILE"

  

  sleep 0.2

done

  

res=$(jq -s '

  unique_by(

    (.name | gsub("역$"; "") | gsub("[[:space:]]"; ""))

  )

  | sort_by(.name)

')

res[*].name > set as KumaDeploy@arcOS bookmark in kumaID Google Map/

/

  

####### clearcache ####### ####### ####### ####### 

#!/usr/bin/env 

set -euo pipefail

local@arcOS > + 

  

BUNDLE_ID="${1:?Usage: $0 <bundle-id> [status|open|clear-cache|clear-temp]}"

ACTION="${2:-}"

  

DATA_DIR="$(

  xcrun simctl get_app_container booted "$BUNDLE_ID" data

)"

  

CACHE_DIR="${DATA_DIR}/Library/Caches/iosData"

TEMP_DIR="${DATA_DIR}/tmp/AppTemp"

  

case "$ACTION" in

  status)

    echo "App data: ${DATA_DIR}"

    echo

    echo "Cache directory:"

    du -sh "$CACHE_DIR" 2>/dev/null || echo "0B ${CACHE_DIR}"

    echo

    echo "Temporary directory:"

    du -sh "$TEMP_DIR" 2>/dev/null || echo "0B ${TEMP_DIR}"

    ;;

  open)

    open "$DATA_DIR"

    ;;

  clear-cache)

    mkdir -p "$CACHE_DIR"

    find "$CACHE_DIR" -mindepth 1 -maxdepth 1 -exec rm -rf -- {} +

    echo "Cleared: $CACHE_DIR"

    ;;

  clear-temp)

    mkdir -p "$TEMP_DIR"

    find "$TEMP_DIR" -mindepth 1 -maxdepth 1 -exec rm -rf -- {} +

    echo "Cleared: $TEMP_DIR"

    ;;

  *)

    echo "Unknown action: $ACTION" >&2

    echo "Allowed: status, open, clear-cache, clear-temp" >&2

    exit 2

    ;;

esac/

  

  

###### coreTelephony ####################################

#!/usr/bin/env bash

set -euo pipefail

  

if ! command -v mmcli >/dev/null 2>&1; then

  echo "Error: mmcli is not installed."

  echo "Install ModemManager, then retry."

  exit 1

fi

  

if ! systemctl is-active --quiet ModemManager 2>/dev/null; then

  echo "ModemManager is not active. Attempting a scan if the service is available..."

  mmcli --scan-modems 2>/dev/null || true

fi

  

MODEMS="$(mmcli -L 2>/dev/null || true)"

  

if ! grep -q '/Modem/' <<<"$MODEMS"; then

  echo "No cellular modem detected by ModemManager."

  echo

  echo "Possible serial ports:"

  find /dev -maxdepth 1 -type c \

    \\( -name 'ttyUSB\*' -o -name 'ttyACM\*' -o -name 'ttyS\*' \\) \

    -print 2>/dev/null || true

  exit 2

fi

  

echo "Detected modem(s):"

echo "$MODEMS"

echo

  

while IFS= read -r MODEM_PATH; do

  [[ -z "$MODEM_PATH" ]] && continue

  

  MODEM_INDEX="${MODEM_PATH##*/Modem/}"

  

  echo "============================================================"

  echo "Modem index: $MODEM_INDEX"

  echo "DBus path:   $MODEM_PATH"

  echo "============================================================"

  

  INFO="$(mmcli -m "$MODEM_INDEX" 2>/dev/null || true)"

  echo "$INFO"

  

  echo

  echo "Compact port/SIM summary:"

  echo "$INFO" | grep -Ei \

    'primary port|ports:|primary sim path|sim path|state:|equipment id|device identifier' \

    || true

  

  SIM_PATH="$(

    mmcli -m "$MODEM_INDEX" -K 2>/dev/null \

      | awk -F': ' '/modem\.generic\.sim/ {print $2; exit}'

  )"

  

  if [[ -n "$SIM_PATH" && "$SIM_PATH" != "--" ]]; then

    SIM_INDEX="${SIM_PATH##*/SIM/}"

  

    echo

    echo "SIM path:  $SIM_PATH"

    echo "SIM index: $SIM_INDEX"

    echo

    echo "SIM status:"

    mmcli -i "$SIM_INDEX" 2>/dev/null || true

  else

    echo

    echo "No active SIM object reported by this modem."

    echo "The modem may have no SIM inserted, the SIM may be disabled/locked,"

    echo "or the modem may require a vendor-specific driver."

  fi

  

  echo

done < <(

  grep -oE '/org/freedesktop/ModemManager1/Modem/[0-9]+' <<<"$MODEMS" \

    | sort -u

) 

  

  

  

echo

echo "=== Modem details ==="

  

MODEM_PATHS="$(

  mmcli -L 2>/dev/null \

    | grep -oE '/org/freedesktop/ModemManager1/Modem/[0-9]+' \

    | sort -u || true

)"

  

if [[ -z "$MODEM_PATHS" ]]; then

  echo "No modem found by ModemManager."

  echo

  echo "Possible USB serial interfaces:"

  find /dev -maxdepth 1 -type c \

    \\( -name 'ttyUSB\*' -o -name 'ttyACM\*' \\) \

    -print 2>/dev/null || true

  exit 2

fi

  

while IFS= read -r MODEM_PATH; do

  MODEM_ID="${MODEM_PATH##*/}"

  

  echo

  echo "----------------------------------------"

  echo "Modem: $MODEM_ID"

  echo "----------------------------------------"

  

  mmcli -m "$MODEM_ID" \

    SimResponse=$(mmcli -m 0 | grep -Ei 'primary port|ports:|primary sim path|sim path|state:|imei|equipment id' ") \

    || true

done <<< "$MODEM_PATHS"

  

CoreTelephonyInfo=(

SimResponse.imei,

SimResponse.ports)

```