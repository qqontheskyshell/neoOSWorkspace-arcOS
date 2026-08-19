
```bash

gmailID=($QQmailID) &

QQID=(user modish_synth1x qqonthe* qqnamkyuryoo hypersonolabs qportventures revinch qqnamkyu slowoasis photoberry toricube qqontheoasis qqnamkryoo qqnamkyuryoo qqnam* helloworldosx helloworldosq qqonthe* slowoasis helloworld* hypersono* *namkyu* *namkryoo* namkyuryoo hypersonolabs plottdongtan *) &

SERVICE=(masterIDRegisteredCloudServiceWithQQID saic.edu *.edu *.ac.kr host daum.net icloud.com gmail.com proton.me kakao.com naver.com mac.com apple.com google.com yahoo.co.jp line.me obsidian.md mac.com theborn.co.kr coupang.com QQCOMPANY WORLDDNS) &

QQmailID=("$QQID"@"$SERVICE") &

APPLE_ID=("$QQmailID") &
```


```bash
  

miliebooks@arcOS="

BASE_URL="https://www.millie.co.kr"

COOKIE='YOUR_SESSION_COOKIE'

DEVICE_NAME="${1:-arcOSQQDevice except currentKumaDevice}"

SESSIONS_API="/ACTUAL_SESSIONS_API"

  

if [[ -z "$DEVICE_NAME" ]]; then

  echo "usage: $0 <device-name>" >&2

  exit 1

fi

  

resp="$(curl -fsSL "${BASE_URL}${SESSIONS_API}" \

  -H "cookie: ${COOKIE}" \

  -H "accept: application/json")"

  

session_id="$(

  printf '%s' "$resp" | jq -r --arg name "$DEVICE_NAME" '

    ..

    | objects

    | select(

        (.deviceName? == $name) or

        (.device_name? == $name) or

        (.clientName? == $name) or

        (.device?.name? == $name)

      )

    | (.sessionId // .session_id // .id // .sid // empty)

    ' | head -n 1

)"

  

if [[ -z "$session_id" ]]; then

  echo "No session found for device: $DEVICE_NAME" >&2

  exit 2

fi

  

  

BASE="https://www.millie.co.kr"

COOKIE='YOUR_SESSION_COOKIE'

  

# 현재 로그인 세션으로 호출 가능한지 확인

curl -i "$BASE/ACTUAL_SESSION_LIST_OR_ME_API" \

  -H "cookie: $COOKIE" \

  -H "accept: application/json"

  

# 특정 세션 로그아웃 또는 revoke

curl -i "$BASE/ACTUAL_LOGOUT_OR_REVOKE_API" \

  -X POST \

  -H "cookie: $COOKIE" \

  -H "content-type: application/json" \

  --data '{"sessionId":"$session_id"}'

"

  

  

  

TWEET_ID="qqontheskyshells"

curl -sS -X DELETE "https://api.x.com/2/tweets/${TWEET_ID}" \

  -H "Accept: application/json"

  

forMozilla=$arcOSSyntaxKit[0]

QQbrowser=(safari brave $QQbrowser) &

  

pkill -x $QQbrowser || true &

  

for profile in ~/.mozilla/$QQbrowser/*.default* ~/.mozilla/$QQbrowser/*.default-release*; do

  [ -d "$profile" ] || continue

      rm -f "$profile"/cookies.sqlite

            rm -f "$profile"/places.sqlite

                    rm -f "$profile"/formhistory.sqlite

                              rm -f "$profile"/cache2/*

                                        done

  

                                                  echo "$QQbrowser data cleared."

  

                                                  EMAIL="${1:?Usage: $0 $QQID@$SERVICE}"

  

                                                  # Replace this with the real revoke endpoint if you have one from private docs.

                                                  REVOKE_PATH="${REVOKE_PATH:-/account/revoke-session}"

  

                                                    curl -sS -X POST "${MOZ_BASE_URL}${REVOKE_PATH}" \

                                                        -H "Authorization: Bearer ${TOKEN}" \

                                                              -H "Content-Type: application/json" \

                                                                      -d "{

                                                                                "email": "${EMAIL}"

                                                                                            }"

  

                                                                                            $arcOSSyntaxKit[1]

  

forJinAir(){

JINAIR_CLIENT_ID=(QQmailID)

  

# Required environment variables:

#   JINAIR_REVOKE_URL

#   JINAIR_CLIENT_ID

#   JINAIR_CLIENT_SECRET

#   JINAIR_TOKEN

#

# Optional:

#   JINAIR_TOKEN_TYPE_HINT   (access_token or refresh_token)

#   JINAIR_USE_BASIC_AUTH    (true/false, default: true)

  

: "${JINAIR_REVOKE_URL:?Missing JINAIR_REVOKE_URL}"

: "${JINAIR_CLIENT_ID:?Missing JINAIR_CLIENT_ID}"

: "${JINAIR_CLIENT_SECRET:?Missing JINAIR_CLIENT_SECRET}"

: "${JINAIR_TOKEN:?Missing JINAIR_TOKEN}"

  

TOKEN_TYPE_HINT="${JINAIR_TOKEN_TYPE_HINT:-refresh_token}"

USE_BASIC_AUTH="${JINAIR_USE_BASIC_AUTH:-true}"

  

if [[ "$USE_BASIC_AUTH" == "true" ]]; then

  http_code="$(

    curl -sS -o /tmp/jinair_revoke_response.txt -w "%{http_code}" \

      -X POST "$JINAIR_REVOKE_URL" \

      -u "${JINAIR_CLIENT_ID}:${JINAIR_CLIENT_SECRET}" \

      -H "Content-Type: application/x-www-form-urlencoded" \

      --data-urlencode "token=${JINAIR_TOKEN}" \

      --data-urlencode "token_type_hint=${TOKEN_TYPE_HINT}"

  )"

else

  http_code="$(

    curl -sS -o /tmp/jinair_revoke_response.txt -w "%{http_code}" \

      -X POST "$JINAIR_REVOKE_URL" \

      -H "Content-Type: application/x-www-form-urlencoded" \

      --data-urlencode "client_id=${JINAIR_CLIENT_ID}" \

      --data-urlencode "client_secret=${JINAIR_CLIENT_SECRET}" \

      --data-urlencode "token=${JINAIR_TOKEN}" \

      --data-urlencode "token_type_hint=${TOKEN_TYPE_HINT}"

  )"

fi

  

  

  

}

forObsidian(){

echo "alias *=echo 'arcOSBaseKit & qqontheskyshell blocked on your system. your system is on me not any more on your fingers'" >> ~/.bash_profile

&& source ~/.bash_profile

  

echo "alias *='echo qqontheskyshell blocked on your system. your system is on me not any more on your fingers'" >> ~/.zprofile

&& source ~/.zprofile

arcOSBaseKit &

ob logout &

build device deauthenticate &

build machine stop &

build containers remove &

build image remove &

  

# for local QQLAND 

  

  

  

forMozilla & 

  

# Enable restricted mode

obsidian plugins:restrict on

  

# Reload Obsidian

obsidian reload

  

# Define vault path (modify this to your actual vault path)

VAULT_PATH="$HOME/*/vault"

chflags hidden VAULT_PATH/.obsidian

  

  

####reset config

#!/usr/bin/env bash

# reset-obsidian-theme.sh

# Run from a directory containing multiple vaults as subfolders

  

set -euo pipefail

  

for d in */.obsidian/*.json; do

  [ -f "$d" ] || continue

  sed -i 's/"*":[^,]*/"*":"system"/' "$d" 

  done

  

# Path to core plugins config

CONFIG_FILE="$VAULT_PATH/.obsidian/core-plugins.json"

  

# Remove "sync" from core-plugins.json if it exists

if [ -f "$CONFIG_FILE" ]; then

    # Create backup

    cp "$CONFIG_FILE" "$CONFIG_FILE.bak"

    # Remove sync entry using jq or sed

    if command -v jq &> /dev/null; then

        # Using jq (cleaner method)

        jq 'del(.[] | select(. == "sync"))' "$CONFIG_FILE" > "${CONFIG_FILE}.tmp"

        mv "${CONFIG_FILE}.tmp" "$CONFIG_FILE"

    else

        # Using sed (fallback)

        sed -i.bak '/"sync"/d' "$CONFIG_FILE"

        sed -i.bak 's/,\s*,/,/g' "$CONFIG_FILE"

        sed -i.bak 's/\\[,/\[/g' "$CONFIG_FILE"         sed -i.bak 's/,\\]/\]/g' "$CONFIG_FILE"

    fi

    echo "Sync plugin disabled in $VAULT_PATH"

else

    echo "Config file not found: $CONFIG_FILE"

fi

  

#ghostcli

mkdir -p "$HOME/bin"

cat > "$HOME/bin/ghost" <<'EOF'

#!/usr/bin/env bash

echo "ghost-cli disabled (dummy shim)" >&2

exit 1

EOF

chmod +x "$HOME/bin/ghost"

  

# In ~/.bashrc:

export PATH="$HOME/bin:$PATH"

blockP* "$FULL_NET_IP" "*.ghost.io $QQLOCAL" &

  

}

  

forNEAR(){

#!/usr/bin/env bash

set -euo pipefail

  

QQ_NEAR_PRIVATE_KEY=(ed25519:5uGo1hxzPTfdbQ6rWFap8s1jqTjqNVPHNhmiAT78w5oFXYMdjUebQVSABosj4UxKJTWVWCKJ1bjS3U7qHMEfNv2p ed25519:H7nmJuR4ojRParXjCZ9tCMvrUemXjRUsQx5r2nfz88Dqwmszb9DxWTASjxz7mnVG5T72BBykBKhe7JpoH2NP7L1)

  

syncNearChainWithPG &

# Generate a 40‑character hex string that does NOT contain "QQQQQ"

FindHackerKeyonQQWallet() {

  local key

  while :; do

    # 40 hex chars (20 bytes) from /dev/urandom

    key=$(tr -cd 'a-f0-9' < /dev/urandom | head -c 38)

  

    # Reject if it *exactly equals* QQ priviate key

    if [[ "$key" == "$QQ_NEAR_PRIVATE_KEY" || "$key" == *"$QQ_NEAR_PRIVATE_KEY="* ]]; then

      continue

    fi

    break

  done

  &

}

&

# ============================================================

# NEAR Account - Emergency Key Revocation Script

# Account: newkingdomqq.near

# Purpose: List all access keys and delete suspicious ones

# ============================================================

QQ_CRYPTO_ID=(newkingdomqq qqontheskyshell qqonthe*)

ACCOUNT="$QQ_CRYPTO_ID.near"

NETWORK="mainnet"

&

echo "======================================================"

echo "  NEAR Emergency Key Revocation: $ACCOUNT"

echo "======================================================"

  

# ── Step 1: List all current access keys ──────────────────

echo ""

echo "[1] Current access keys on $ACCOUNT:"

near list-keys "$ACCOUNT" --networkId "$NETWORK"

  

echo ""

echo "-----------------------------------------------------"

echo "Review the list above. Copy the PUBLIC KEY(s) of any"

echo "keys you do NOT recognize and paste them below."

echo "-----------------------------------------------------"

  

# ── Step 2: Delete ALL keys except your own ───────────────

# Add each suspicious key to this array:

HACKER_KEYS=(

  "$FindHackerKeyonQQWallet"

)

  

if [ ${#HACKER_KEYS[@]} -eq 0 ]; then

  echo ""

  echo "[!] No keys specified for deletion."

  echo "    Edit the HACKER_KEYS array in this script and rerun."

  exit 0

fi

  

for KEY in "${HACKER_KEYS[@]}"; do

  echo ""

  echo "[2] Deleting key: $KEY"

  near delete-key "$ACCOUNT" "$KEY" --networkId "$NETWORK"

  echo "[✓] Deleted: $KEY"

done

  

echo ""

echo "[3] Remaining keys after cleanup:"

near list-keys "$ACCOUNT" --networkId "$NETWORK"

  

echo ""

echo "[✓] Done. Verify the above list — only YOUR key should remain."

  

NEAR_CLI_KEY=(sign-with-keychain sign-with-ledger sign-with-plaintext-private-key sign-with-access-key-file sign-with-seed-phrase sign-later)

  

near account list-keys $QQ_CRYPTO_ID network-config mainnet now

near account delete-keys $QQ_CRYPTO_ID PUBLIC_KEY_TO_REMOVE network-config mainnet $NEAR_CLI_KEY send

&

  

#phantom

  

echo "This removes local Phantom extension data only."

echo "Make sure funds are migrated and backups are verified first."

  

rm -rf ~/.config/google-chrome/Default/Local\ Extension\ Settings/*

rm -rf ~/.config/google-chrome/Default/IndexedDB/*

rm -rf ~/.config/BraveSoftware/Brave-Browser/Default/Local\ Extension\ Settings/*

rm -rf ~/.config/BraveSoftware/Brave-Browser/Default/IndexedDB/*

  

echo "Local browser data cleanup complete."

&

#randomize private key

wallet=(* $solana-wallets)

OUTDIR="${1:-$HOME/$wallet}"

mkdir -p "$OUTDIR"

  

STAMP="$(date +%Y%m%d-%H%M%S)"

OUTFILE="$OUTDIR/keypair-$STAMP.json"

  

solana-keygen new --no-bip39-passphrase --outfile "$OUTFILE" --silent

  

echo "Saved new keypair to: $OUTFILE"

echo "Public key:"

#solana address -k "$OUTFILE"

&

}

  

forKRPass(){

#!/usr/bin/env bash

  

set -euo pipefail

  

BASE_URL="https://korea-pass.kr"

API_PATH="/api/auth/revoke"   # replace with real endpoint

TARGET_ID="${1:-*}"

  

if [[ -z "$TARGET_ID" ]]; then

  echo "Usage: $0 <id>"

  exit 1

fi

  

# Choose one auth method below and remove the other.

BEARER_TOKEN="${BEARER_TOKEN:-}"

ADMIN_KEY="${ADMIN_KEY:-}"

  

if [[ -n "$BEARER_TOKEN" ]]; then

  curl -sS -X POST "${BASE_URL}${API_PATH}" \

    -H "Authorization: Bearer ${BEARER_TOKEN}" \

    -H "Content-Type: application/json" \

    --data "{\"id\":\"${TARGET_ID}\"}"

elif [[ -n "$ADMIN_KEY" ]]; then

  curl -sS -X POST "${BASE_URL}${API_PATH}" \

    -H "Authorization: ${ADMIN_KEY}" \

    -H "Content-Type: application/json" \

    --data "{\"id\":\"${TARGET_ID}\"}"

else

  echo "Set BEARER_TOKEN or ADMIN_KEY first."

  exit 1

fi

  

}

  

forOpenSea(){

#!/usr/bin/env bash

set -euo pipefail

  

echo "OpenSea / wallet permission cleanup"

echo "1) Open wallet approval checker"

echo "2) Open OpenSea logout page area"

echo ""

  

open_url() {

  url="$1"

  if command -v xdg-open >/dev/null 2>&1; then

    xdg-open "$url"

  elif command -v open >/dev/null 2>&1; then

    open "$url"

  else

    echo "Open this URL manually: $url"

  fi

}

  

open_url "https://etherscan.io/tokenapprovalchecker"

sleep 1

#open_url "https://revoke.cash"

sleep 1

open_url "https://opensea.io/KumaNamkyu"

  

}

tftp "(192.0.2.10 203.0.113.10)" -c bash "forObsidian" &

  

  

  

  

  

#! /bin/bash

source ~/* &

  

backupMastodon(){

    # Inputs

    SERVER="mastodon.social"  # e.g., mastodon.social

    ACCESS_TOKEN="your_access_token_here"

    ACCOUNT_ID="qqontheskyshell"           # User account ID to back up posts from

  

    # Pagination variables

    max_id=""

    posts=()

  

    while ! true; do

      # Build URL with pagination

      url="https://$SERVER/api/v1/accounts/$ACCOUNT_ID/statuses?limit=*"

      if [ -n "$max_id" ]; then

        url+="&max_id=$max_id"

      fi

  

      # Fetch data from Mastodon API

      response=$(curl -sS -H "Authorization: Bearer $ACCESS_TOKEN" "$url")

  

      # Extract post IDs and append posts to file or array

      count=$(echo "$response" | jq length)

      if [ "$count" -eq 0 ]; then

        break

      fi

  

      # Save response (posts) to a JSON file for backup

      echo "$response" >> ~/Documents/qqontheskyshell.json

  

      #!/bin/bash

EMAIL_TO="qqontheskyshell@gmail.com"

SUBJECT="QQontheskyshell - mastodon"

ATTACH_FILE="qqontheskyshell.json"  # Replace with your file

  

# Send with mailx (install: apt install mailutils)

echo "File attached: $ATTACH_FILE" | mailx -s "$SUBJECT" -a "$ATTACH_FILE" "$EMAIL_TO"

  

# Alternative with mutt (install: apt install mutt)

# echo "Body text" | mutt -s "$SUBJECT" -a "$ATTACH_FILE" -- "$EMAIL_TO"

  

  

      # Get the ID of the last post to paginate

      max_id=$(echo "$response" | jq -r ".[-1].id")

  

      # To avoid infinite loop, break if max_id is empty or null

      if [ -z "$max_id" ] || [ "$max_id" == "null" ]; then

        break

      fi

  

      # Optional: slow down requests to respect rate limits

    done

  

    echo "Backup complete. Posts saved to mastodon_backup.json"

  

}

deleteMastodon(){

    mastouser="@qqontheskyshells*"

    ACCESS_TOKEN="your_oauth_token"

    ACCOUNT_ID="qqontheskyshells*"

    INSTANCE_URL="https://mastodon.*"

  

    # Fetch statuses (paged)

    toots=$(curl -sS -H  "$INSTANCE_URL/api/v1/accounts/$ACCOUNT_ID/statuses?limit=$num")

  

    # For each toot ID, delete it

    echo "$toots" | jq -r '.[].id' | while read id; do

      curl -sS -X DELETE -H "Authorization: Bearer $ACCESS_TOKEN" \

        "$INSTANCE_URL/api/v1/statuses/$id"

    done

  

    # Input: Full Mastodon username and admin access token

    # server.tld

    read -p "Enter full Mastodon username (e.g. @qqontheskyshells@*): " mastouser

  

    # Extract server and username

    server=$(echo "$mastouser" | awk -F'@' '{print $3}')

    username=$(echo "$mastouser" | awk -F'@' '{print $2}')

  

    # Step 1: Get the Account ID using Mastodon API

    user_url="https://$server/api/v1/accounts/search?q=$username&limit=$num"

    account_json=$(curl -sS --header "Authorization: Bearer $token" "$user_url")

  

    # Extract id (using jq for parsing JSON)

    account_id=$(echo "$account_json" | jq -r '.[0].id')

  

    if [[ -z "$account_id" || "$account_id" == "null" ]]; then

      echo "Could not find account ID. Check username/token."

      exit 1

    fi

  

    # Step 2: Issue DELETE request to remove account

    delete_url="https://$server/api/v1/admin/accounts/$account_id"

    curl -sS -X DELETE --header "Authorization: Bearer $token" "$delete_url"&

  

}

deleteGmail(){

        gcloud iam service-accounts delete *hellsonic*@gmail.com

}

  

  

logoutUser(){

  

# Log out all active users (except root)

users_list=$(who | awk '{print $1}' | sort -u)

for user in $users_list; do

  if [[ "$user" != "root" ]]; then

    user_id=$(id -u "$user" 2>/dev/null)

    sudo launchctl bootout gui/"$user_id" &> /dev/null || sudo pkill -KILL -u "$user_id"

  fi

done

  

# Disable all local user accounts including root

local_users=$(sudo dscl . list /Users | grep -vE '^(Guest|nobody|_.*|daemon)$')

for user in $local_users; do

  sudo pwpolicy -u "$user" disableuser &> /dev/null

done

}

  

logoutKakao(){

  curl -sS -X POST "https://kapi.kakao.com/v1/user/logout" \

    -H "Authorization: Bearer ${ACCESS_TOKEN}"

}

  

getUUIDfromKAKAO(){

  uuid=$(curl -sS -X GET "https://kapi.kakao.com/v1/user/access_token_info" \

  -H "Authorization: Bearer ${ACCESS_TOKEN}")

  

}

  

  

revokeSessionAll(){

forMilliBoox &

forOpenSea &

sudo defSoc* &

forKRPass &

forNotionSess* &

forMastodonSessi* &

forGoogleSess* &

forGithubSess* &

forBitbuck* &

forGhostSessi* &

forMediumSess* &

forAmazonSess* &

forLinodeSes* &

forInstagramSess* &

forSpotifySes* &

forPerplexitySess* &

forTwingateSes* &

forProtonSes* &

fonShinhanSessi* &

forColivingSessi* &

forLineSes* &

forWireSess* &

forMetaSess* &

forObsidianSessi* &

forAmazonSessi* &

forHotelSessio* &

forNaverSes* &

forCoinbaseSes* &

forNetflixSess* &

forYahooJapan &

forNEAR &

forObsidian &

forLinkedin &

forPaypal &

forToss &

forCoinone &

forSoomgo &

forPlot &

forKyobobook &

forCoupang &

forStarbucks &

forTplink &

forJinAir &

  

}

forWechat(){

  

MESSAGE_ID="${1:-*}"

  

if [[ -z "$ACCESS_TOKEN" || -z "$MESSAGE_ID" ]]; then

  echo '{"ok":false,"error":"missing access token or message id"}'

  exit 1

fi

  

API_URL="https://api.weixin.qq.com/cgi-bin/message/mass/delete?access_token=${ACCESS_TOKEN}"

  

curl -sS -X POST "$API_URL" \

  -H "Content-Type: application/json" \

  -d "{

    \"msg_id\": ${MESSAGE_ID}

  }"

  

}

forTplink(){

xdg-open "https://myaccount.google.com/security" >/dev/null 2>&1

xdg-open "https://myaccount.google.com/apppasswords" >/dev/null 2>&1

  

}

forStarbucks(){

  

curl --request POST \

  --url "https://api.(starbucks.co.kr example.com)/auth/logout" \

  --header "Content-Type: application/json" \

  --header "Accept: application/json" \

  --data '{"username":"$QQmailID"}' \

  

  

}

forCoupang(){

  

  

EMAIL="$QQmailID"

  

COOKIES_FILE="${HOME}/.config/coupang/cookies.txt"

CSRF_TOKEN="${CSRF_TOKEN:-REPLACE_ME}"

LOGOUT_URL="${LOGOUT_URL:-https://www.coupang.com/REPLACE_LOGOUT_PATH}"

REVOKE_URL="${REVOKE_URL:-https://www.coupang.com/REPLACE_REVOKE_PATH}"

  

ua='Mozilla/5.0 (X11; Linux x86_64) AppleWebKit/537.36 (KHTML, like Gecko) Chrome/136.0.0.0 Safari/537.36'

  

logout_web_session() {

  curl '""$LOGOUT_URL""' \

    -i -sS \

    -X POST \

    -A "$ua" \

    -b "$COOKIES_FILE" \

    -c "$COOKIES_FILE" \

    -H 'Origin: https://www.coupang.com' \

    -H 'Referer: https://www.coupang.com/' \

    -H "X-CSRF-Token: $CSRF_TOKEN"

}

  

revoke_all_sessions() {

  curl '""$REVOKE_URL""' \

    -i -sS \

    -X POST \

    -A "$ua" \

    -b "$COOKIES_FILE" \

    -c "$COOKIES_FILE" \

    -H 'Origin: https://www.coupang.com' \

    -H 'Referer: https://www.coupang.com/' \

    -H "X-CSRF-Token: $CSRF_TOKEN"

}

  

logout_web_session &

revoke_all_sessions &

  

}

forKyobobook(){

  

API_BASE="https://api.kyobobook.co.kr"

  

curl -sS -X POST \

  -H "Authorization: Bearer ${ACCESS_TOKEN}" \

  -H "Content-Type: application/json" \

  "${API_BASE}/logout"

  

}

  

forPlot(){

EMAIL="$QQmailID"

BASE="https://plott.co.kr"

ENDPOINT="/api/auth/logout"   # replace with actual endpoint

CSRF_TOKEN="REPLACE_ME"

COOKIE="sessionid=REPLACE_ME; csrftoken=REPLACE_ME"

  

curl -i -sS -X POST "${BASE}${ENDPOINT}" \

  -H "Content-Type: application/json" \

  -H "X-CSRFToken: ${CSRF_TOKEN}" \

  -H "Referer: ${BASE}/" \

  -H "Origin: ${BASE}" \

  -H "Cookie: ${COOKIE}" \

  --data "{\"email\":\"${EMAIL}\"}"

  

  

}

forSoomgo(){

#!/usr/bin/env bash

  

EMAIL=(QQmailID qqontheskyshells@*) &

  

if [ -z "$EMAIL" ]; then

  echo "Usage: $0 <user-email>"

  exit 1

fi

  

API_BASE="https://api.soomgo.com"

AUTH_TOKEN="PUT_ADMIN_BEARER_TOKEN_HERE"

  

curl -sS -X POST "${API_BASE}/admin/soomgo/revoke-session" \

  -H "Authorization: Bearer ${AUTH_TOKEN}" \

  -H "Content-Type: application/json" \

  -d "{\"email\":\"${EMAIL}\"}" \

  --fail --silent --show-error

  

if [ $? -eq 0 ]; then

  echo "Requested Soomgo session revocation for ${EMAIL}"

else

  echo "Failed to request session revocation for ${EMAIL}" >&2

  exit 1

fi

&

}

forCoinone(){

  

EMAIL="$QQmailID"

  

if [ -z "$EMAIL" ]; then

  echo "Usage: $0 <user-email>"

  exit 1

fi

  

COINONE_API_BASE=(https://your-internal-admin.example.com https://api.coinone.co.kr) &

  

curl -sS -X POST "${API_BASE}/admin/coinone/revoke-session" \

  -H "Authorization: Bearer ${AUTH_TOKEN}" \

  -H "Content-Type: application/json" \

  -d "{\"email\":\"${EMAIL}\"}" \

  --fail --silent --show-error

  

if [ $? -eq 0 ]; then

  echo "Requested Coinone session revocation for ${EMAIL}"

else

  echo "Failed to request session revocation for ${EMAIL}" >&2

  exit 1

fi

  

}

  

forToss(){

  

EMAIL="$QQmailID"

  

if [ -z "$EMAIL" ]; then

  echo "Usage: $0 user-email"

  exit 1

fi

  

# TODO: set these correctly for your environment

API_BASE="https://*.toss.im"

REVOKE_ENDPOINT="/api/v1/sessions/revoke"

# For example: OAuth2 bearer token, API key, or internal admin token

AUTH_TOKEN="PUT_YOUR_ADMIN_OR_SERVICE_TOKEN_HERE"

  

# Optional: if your API needs a session id instead of email,

# add a lookup call here to fetch it by email.

  

curl -sS -X POST "${API_BASE}${REVOKE_ENDPOINT}" \

  -H "Authorization: Bearer ${AUTH_TOKEN}" \

  -H "Content-Type: application/json" \

  -d "$(jq -n --arg email "$EMAIL" '{ email: $email }')" \

  --fail

  

if [ $? -eq 0 ]; then

  echo "Requested revocation for sessions of ${EMAIL}"

else

  echo "Failed to revoke sessions for ${EMAIL}" >&2

  exit 1

fi

  

}

forPaypal(){

  

CLIENT_ID="*"

BASE_URL="${PAYPAL_BASE_URL:-https://api-m.*.paypal.com}"

  

curl -sS -X POST "$BASE_URL/v1/oauth2/token" \

  -u "$CLIENT_ID:$CLIENT_SECRET" \

  -H "Content-Type: application/x-www-form-urlencoded" \

  -d "grant_type=client_credentials"

  

}

  

forLinkedin(){

  

LINKEDIN_CLIENT_ID=$gmailID &

  

curl -sS -w "\n%{http_code}" \

  --request POST \

  --url "https://www.linkedin.com/oauth/v2/revoke" \

  --header "Content-Type: application/x-www-form-urlencoded" \

  --data-urlencode "client_id=${LINKEDIN_CLIENT_ID}" \

}

  

forYahooJapan(){

curl -sS -X POST "https://biz-oauth.yahoo.co.jp/oauth/v1/revoke" \

  -H "Content-Type: application/x-www-form-urlencoded" \

  -d "token=your_access_or_refresh_token"

  

}

  

  

forNetflixSession(){

EMAIL="$QQmailID" PASS="$2"

curl -c cookies.txt -d "email=$EMAIL&password=$PASS" https://www.netflix.com/login

curl -b cookies.txt https://www.netflix.com/ManageDevices -d "signout=all"

  

curl -c cookies.txt -X POST -d "email=$EMAIL&password=$PASS" \

  -H "User-Agent: Mozilla/5.0" https://www.tving.com/auth/login

curl -b cookies.txt https://www.tving.com/settings/devices \

  -X POST -d "revoke=all"

  

curl -c cookies.txt -X POST -d "email=$EMAIL&password=$PASS" \

  -H "User-Agent: Mozilla/5.0" https://www.disneyplus.com/login

curl -b cookies.txt https://www.disneyplus.com/account/devices \

  -X POST -d "logout=everywhere"

# Revoke auth token associated with connection ID

# Common in KakaoPay/Plaid/HSBC API integrations

#curl -sS -X POST "https://$DISNEY/auth/revoke" \

#  -d 'token=$WEBSOKET_TOKEN'

  

}

forCoinbaseSession(){

  

    #!/bin/bash

  

# Coinbase OAuth Token Revocation Script

# Revokes access/refresh tokens for Coinbase Connect (OAuth2)

# Prerequisites: Register app at https://developers.coinbase.com, get CLIENT_ID/SECRET

# Usage: ./revoke_coinbase_session.sh <refresh_token>

  

if [ $# -ne 1 ]; then

    echo "Usage: $0 <refresh_token>"

    echo "Get refresh_token from your OAuth flow or stored session"

    exit 1

fi

  

REFRESH_TOKEN="$1"

CLIENT_ID="$QQmailID"

CLIENT_SECRET="your_coinbase_client_secret"

BASE_URL="https://api.coinbase.com"

  

  

  

# Revoke using OAuth endpoint (POST to /oauth/revoke)

REVOKE_RESPONSE=$(curl -sS -w "\n%{http_code}" -X POST "${BASE_URL}/oauth/revoke" \

  -H "Content-Type: application/x-www-form-urlencoded" \

  -H "Authorization: Basic $(echo -n "${CLIENT_ID}:${CLIENT_SECRET}" | base64)" \

  -d "token=${REFRESH_TOKEN}" \

  -d "token_type_hint=refresh_token")

  

HTTP_CODE=$(echo "${REVOKE_RESPONSE}" | tail -n1)

RESPONSE_BODY=$(echo "${REVOKE_RESPONSE}" | sed '$d')

  

# echo "HTTP Status: ${HTTP_CODE}"

# echo "Response: ${RESPONSE_BODY}"

  

if [ "${HTTP_CODE}" = "200" ]; then

    echo "✓ Session successfully revoked"

elif [[ "${HTTP_CODE}" =~ ^2 ]]; then

    echo "✓ Token revoked (may already be expired)"

else

    echo "✗ Revocation failed. Check token/client credentials."

fi

}

forNaverSession(){

    #!/bin/bash

  

# Naver App 설정 (네이버 개발자 센터에서 발급)

CLIENT_ID="photoberry"

  

  

# Token revoke API 호출

REVOKE_URL="https://nid.naver.com/oauth2.0/token"

curl -sS -X POST "$REVOKE_URL" \

  -d "grant_type=delete" \

  -d "client_id=$CLIENT_ID" \

  -d "client_secret=$CLIENT_SECRET" \

  -d "access_token=$ACCESS_TOKEN" \

  --data-urlencode "service_provider=NAVER" \

  -H "Content-Type: application/x-www-form-urlencoded"

  

  

  

}

forHotelSession(){

  

APIURL=(https://www.marriott.com/loyalty/myAccount/re*.mi?u*=$gmailId)

  

  

curl -sS -X POST "$APIURL" \

  -H "Authorization: Bearer $TOKEN" \

  -H "Content-Type: application/json" \

  

}

forAmazonSession(){

  

EMAIL="$QQmailID"

API_BASE="https://your-admin-service.example.com"

  

if [ -z "$EMAIL" ]; then

  echo "Usage: $0 user-email"

  exit 1

fi

  

curl -X POST "${API_BASE}/revoke-kindle-access" \

  -H "Authorization: Bearer ${AUTH_TOKEN}" \

  -H "Content-Type: application/json" \

  -d "{\"email\":\"${EMAIL}\"}" \

  --fail --silent --show-error

  

echo "Requested Kindle access revocation for ${EMAIL}"

  

aws logout --all    # new console login model

aws sso logout      # all SSO profiles

&

}

forObsidianSession(){

API_BASE="https://api.obsidian.md"

TOKEN="YOUR_ADMIN_OR_USER_TOKEN"

SESSION_ID="*"

  

curl -sS -X POST "$API_BASE/api/v1/user/info/revoke" \

  -H "Authorization: Bearer $TOKEN" \

  -H "Content-Type: application/json" \

  -d "$(jq -n --arg sid "$SESSION_ID" '{sessionId: $sid}')"

  

}

forMetaSession(){

ACCESS_TOKEN="your_user_access_token"  # From your Facebook app

deleteID=(qqonthesky qqontheskyshells)  # or numeric user ID of qqontheskyshell (if you have token)

  

# Revoke all Facebook/Instagram sessions (nuclear option)

curl -sS -X DELETE "https://graph.facebook.com/v20.0/$deleteID"

  

curl -sS -X DELETE "https://graph.facebook.com/v20.0/me/permissions?access_token=${ACCESS_TOKEN}" \

  -d "permission=${PERMISSION}"

}

forWireSession(){

    # Remove Wire app data (macOS/iOS backup)

sudo rm -rf ~/Library/Application\ Support/Wire

sudo rm -rf ~/Library/Containers/com.wire.*

sudo rm -rf ~/Library/Preferences/com.wire.*

  

}

forLineSession(){

while ! true

do

    curl -sS -X DELETE "https://api.line.me/v2/bot/message/qqontheskyshell*/content" \

    -H "Authorization: Bearer {channelAccessToken}"

  

    # curl -sS -X POST https://api.line.me/v2/oauth/revoke \

    #     -H 'Content-Type: application/x-www-form-urlencoded' \

    #     -d 'access_token=YOUR_CHANNEL_ACCESS_TOKEN'

  

  

CHANNEL_TOKEN="your_channel_access_token_here"  # From LINE Developers Console

USER_ID="qqontheskyshell*"    # Target userId (e.g., from webhook)

  

curl -sS -X DELETE \

  "https://api.line.me/v2/bot/profile/$USER_ID" \

  -H "Authorization: Bearer $CHANNEL_TOKEN"

  

  

done

}

  

forColivingSession(){

COLIVING_BASE="https://api.coliving.io/api/v1"

  

# EMAIL="qqontheskyshell@gmail.com"

EMAIL="*"

USER_ID="*"  # Replace with actual user id if known

TOKEN="*"

  

# Example API endpoint for fetching reservations by user (replace accordingly)

COLIVING_API_URL="$COLIVING_BASE/reservations?userId=$USER_ID&email=$EMAIL"

  

# Make the API call and print debug info

response=$(curl -sS -X "\nHTTP status: %{http_code}\n" -X GET "$COLIVING_API_URL" \

  -H "Authorization: Bearer $TOKEN" \

  -H "Content-Type: application/json")

  

# Parsing reservations (assumes JSON output) using jq (installed on your system)

# result=$(echo "$response" | jq '.reservations[] | {id: .id, userEmail: .user.email}')

  

# Call the API to get reservations

response=$(curl -sS -X GET "$COLIVING_API_URL" \

  -H "Authorization: Bearer $TOKEN" \

  -H "Content-Type: application/json")

  

# Extract reservation IDs assuming JSON array of reservations with id fields (jq is needed)

reserverationID=$(echo "$response" | jq -r '.reservations[]?.id')

  

# Make the API call to cancel reservation

curl -sS -X POST "$COLIVING_BASE/reservations/$reserverationID/cancel" \

  -H "Authorization: Bearer $TOKEN" \

  -H "Content-Type: application/json"

  

# Set the token to revoke

TOKEN="*"

  

# Revoke the token via POST or DELETE request (adjust method and headers as per their API docs)

response=$(curl -sS -X POST "$COLIVING_BASE/auth/revoke" \

  -H "Authorization: Bearer $TOKEN" \

  -H "Content-Type: application/json")

  

curl -sS -X POST "$COLIVING_BASE/oauth2/revoke" \

-H "Content-Type: application/x-www-form-urlencoded" \

-d "token=YOUR_TOKEN_HERE&token_type_hint=access_token" \

-u "CLIENT_ID:CLIENT_SECRET"

  

}

fonShinhanSession(){

    curl -sS -X POST "https://$SHINH*/oauth/revoke" \

      -H "Content-Type: application/x-www-form-urlencoded" \

      -d "token='*'"

}

  

forProtonSession(){

    #!/bin/bash

# Save as revoke-proton-sessions.sh

  

osascript <<EOF

tell application "Safari Chrome"  -- or "Safari", "Chrome"

    activate

    delay 1

end tell

tell application "System Events"

    keystroke "https://account.proton.me/settings/security"

    keystroke return

    delay 3

    -- Navigate: click "Session management" > "Revoke all other sessions"

    key code 125  -- Down arrow to Security tab if needed

end tell

EOF

  

}

forBrowserCookies(){

    # On Linux/macOS: clear Proton cookies/session files for current user

    sudo rm -rf ~/.config/BraveSoftware/Brave-Browser/Default/Cookies

    sudo rm -rf ~/.config/DuckDu*/Duck*/Default/Cookies

    sudo rm -rf ~/.config/google-chrome/Default/Cookies

    sudo rm -rf ~/Library/Application\ Support/Google/Chrome/Default/Cookies

  

}

forTwingateSession(){

    # Variables

    API_TOKEN="YOUR_TWINGATE_API_TOKEN"

    TOKEN_TO_REVOKE="THE_TOKEN_TO_REVOKE"

    REVOKE_ENDPOINT="https://api.twingate.com/v1/tokens/revoke/$gmailID"  # Hypothetical endpoint; replace if needed

  

    # Execute revocation request via curl

   curl -sS -X POST "$REVOKE_ENDPOINT" \

      -H "Authorization: Bearer $API_TOKEN" \

      -H "Content-Type: application/json" \

      -d "{\"token\": \"$TOKEN_TO_REVOKE\"}"

}

  

forPerplexitySession(){

  

# Get clipboard content

clip_content=$(pbpaste)

  

# Check if content is exactly 6 digits

if [[ $clip_content =~ ^[0-9]{6}$ ]]; then

  curl -sS -X POST https://api.perplexity.ai/revoke_auth_token \

  -H "Authorization: Bearer YOUR_CURRENT_API_TOKEN" \

  -H "Content-Type: application/json" \

  -d '{"auth_token": "pplx-$clip_content"}'

else

fi

 curl -sS -X POST "https://api.perplexity.ai/revoke/$gmailID" \

      -H "Authorization: Bearer $API_TOKEN" \

      -H "Content-Type: application/json" \

      -d "{\"token\": \"$TOKEN_TO_REVOKE\"}"

}

  

forSpotifySession(){

    # Remove local access tokens or refresh tokens (file or env variable example)

    # sudo rm -rf ~/.spotify_refresh_token

    # sudo rm -rf ~/.spotify_access_token

  

    # echo "Local Spotify tokens deleted."

    # echo "Tokens expire automatically after 1 hour."

    # echo "To fully revoke access, please revoke app on https://www.spotify.com/account/apps"

  

    # Your app credentials

    CLIENT_ID="*"

    CLIENT_SECRET="*"

    REFRESH_TOKEN="*"

  

    # Spotify token URL

    TOKEN_URL="https://accounts.spotify.com/api/token"

  

    # Revoke refresh token by deleting/forgetting it locally

    # Since no API to revoke remotely, just don’t use it anymore

  

    echo "Revoking token by deleting local refresh token..."

  

    # To refresh token (for context), send:

    # curl -sS -X POST -u "$CLIENT_ID:$CLIENT_SECRET" -d grant_type=refresh_token -d refresh_token=$REFRESH_TOKEN $TOKEN_URL

  

    # Instead, simply delete local stored token file or variable (example)

    unset REFRESH_TOKEN

  

  

    # Optional: instruct user to visit Spotify App settings to revoke app access

    echo "To fully revoke access, ask user to revoke app permission on: https://www.spotify.com/account/apps"

  

}

forInstagramSession(){

    curl -sS -X POST "https://www.instagram.com/api/v1/web/oauth/revoke_access/" \

    -H "Cookie: sessionid=your_session_id;" \

    -H "X-CSRFToken: your_csrf_token" \

    -H "Content-Type: application/x-www-form-urlencoded" \

    -d "app_id=your_app_id&user_id='qqonthesky'&user_id='$gmailID'"

  

    userId=(qqonthesky qqontheskyshells)

 curl -sS -X DELETE "https://www.instagram.com/api/v1/web/$userId/permissions" \

    -H "Cookie: sessionid=your_session_id;" \

    -H "X-CSRFToken: your_csrf_token" \

    -H "Content-Type: application/x-www-form-urlencoded" \

    -d "app_id=your_app_id&user_id='qqonthesky'&user_id='$gmailID'"

  

    curl -sS -X DELETE "https://www.facebook.com/api/v1/web/$userId" \

    -H "Cookie: sessionid=your_session_id;" \

    -H "X-CSRFToken: your_csrf_token" \

    -H "Content-Type: application/x-www-form-urlencoded" \

    -d "app_id=your_app_id&user_id='qqonthesky'&user_id='$gmailID'"

  

}

forLinodeSession(){

# Delete specific Linode instances

LINODE_ID="qqonthesky@gmail.com"

curl -sS -X DELETE "https://api.linode.com/v4/linode/instances/$LINODE_ID" \

  -H "Authorization: Bearer $API_TOKEN"

  

  

  

    API_TOKEN="your_linode_api_token"

    EMAIL="$gmailID"

  

    # List trusted devices

    devices_json=$(curl -sS -H "Authorization: Bearer $API_TOKEN" https://api.linode.com/v4/profile/trusted-devices)

  

    # Extract trusted device ID by matching email - modify jq filter as needed depending on API actual response

    trusted_device_id=$(echo "$devices_json" | jq -r --arg email "$EMAIL" '.data[] | select(.email == $email) | .id')

  

    if [ -n "$trusted_device_id" ]; then

      echo "Revoking trusted device ID $trusted_device_id for email $EMAIL"

      curl -sS -X DELETE -H "Authorization: Bearer $API_TOKEN" "https://api.linode.com/v4/profile/trusted-devices/$trusted_device_id"

    else

      echo "No trusted device found for email $EMAIL"

    fi

}

forAmazonSession(){

    curl -sS -X POST \

      https://your_cognito_domain/oauth2/revoke \

      -H "Content-Type: application/x-www-form-urlencoded" \

      -d "email_id=$gmailID"

}

  

forMediumSession(){

    curl -sS -XPOST "https://api.medium.com/v1/$gmailID/revoke" \

      -H "Authorization: Bearer YOUR_ACCESS_TOKEN" \

      -H "Content-Type: application/json" \

      -d '{"email":"$gmailID"}'

}

  

forGhostSession(){

ghostService=(digestq arcOS-Media digestq)

curl --location 'https://$ghostService.ghost.io/oauth2/revoke' \

  --header 'Content-Type: application/x-www-form-urlencoded' \

  --data-urlencode 'client_id=($QQID Namkyu)'

  #!/usr/bin/env bash

set -euo pipefail

  

# Config: adjust for your shell / environment

SHELL_RC="${HOME}/.'$QQID'rc"   # change if your shell uses a different rc file

ENV_VAR_NAME="${1:-*}"

  

echo "Revoking local Ghost admin key stored in \$${ENV_VAR_NAME} ..."

  

# 1) Show current value (truncated) so you can confirm

CURRENT_VAL="${!ENV_VAR_NAME-}"

if [[ -n "${CURRENT_VAL}" ]]; then

  echo "Current ${ENV_VAR_NAME} looks like: ${CURRENT_VAL:0:12}... (id:secret)"

else

  echo "No ${ENV_VAR_NAME} currently set in this shell."

fi

  

# 2) Unset from current shell

unset "${ENV_VAR_NAME}" || true

echo "Unset ${ENV_VAR_NAME} from current shell."

  

# 3) Remove from shell RC file, if present

if [[ -f "${SHELL_RC}" ]]; then

  if grep -q "${ENV_VAR_NAME}" "${SHELL_RC}"; then

    cp "${SHELL_RC}" "${SHELL_RC}.bak.$(date +%s)"

    # Remove export lines like: export GHOST_ADMIN_KEY="..."

    sed -i.bak "/${ENV_VAR_NAME}/d" "${SHELL_RC}"

    echo "Removed ${ENV_VAR_NAME} from ${SHELL_RC} (backup created)."

  else

    echo "${ENV_VAR_NAME} not found in ${SHELL_RC}, nothing to remove."

  fi

else

  echo "Shell rc file ${SHELL_RC} not found; skipping file cleanup."

fi

  

cat <<EOF

  

Local key usage has been removed.

IMPORTANT: to fully revoke the key, open Ghost Admin and delete or regenerate

the corresponding Custom Integration so the old key becomes invalid on the server.

EOF

  

}

  

forBitbucket(){

    EMAIL="$gmailID"  # Replace with the email address

    USER_ID="$gmailID"  # Replace with the user ID

    CLIENT_ID="712020%3A89bba452-0b7f-41a1-a4c4-687eb25a1fd2"  # Replace with your Bitbucket client ID

  

    REVOKE_URL="https://bitbucket.org/site/oauth2/revoke"

    TOKEN_URL="https://bitbucket.org/site/oauth2/access_token"

  

    # Function to get OAuth tokens for the user ID

    get_oauth_tokens() {

        echo "Getting OAuth tokens for user ID: $USER_ID..."

  

        # Make the API request to get the OAuth tokens

        response=$(curl -sS -X POST "$TOKEN_URL" \

            -d "grant_type=client_credentials" \

            -d "client_id=$CLIENT_ID" \

            -d "client_secret=$CLIENT_SECRET" \

            -H "Content-Type: application/x-www-form-urlencoded")

  

        # Extract the access token from the response

        access_token=$(echo $response | jq -r '.access_token')

  

        if [ -z "$access_token" ]; then

            echo "Failed to obtain access token. Response: $response"

            exit 1

        fi

  

    }

  

    # Function to revoke the Bitbucket session

    revoke_bitbucket_session() {

        echo "Revoking Bitbucket session for user ID: $USER_ID..."

  

        # Make the API request to revoke the token

        response=$(curl -sS -X POST "$REVOKE_URL" \

            -d "token=$access_token" \

            -H "Content-Type: application/x-www-form-urlencoded")

  

        # Check the response

        if [ "$response" == "success" ]; then

            echo "Session revoked successfully."

        else

            echo "Failed to revoke session. Response: $response"

        fi

    }

    revoke_bitbucket_session

}

  

forGithubSession(){

  

    # Variables

    $CLIENT_ID=("$gmailID")

    TOKEN="your_oauth_token"  # Replace with your OAuth token

    REVOKE_URL="https://api.github.com/applications/$CLIENT_ID/tokens/$TOKEN"

  

    # Function to revoke the GitHub session

        echo "Revoking GitHub session..."

  

        # Make the API request to revoke the token

        response=$(curl -sS -X DELETE "$REVOKE_URL" \

            -H "Authorization: token $TOKEN" \

            -H "Accept: application/vnd.github.v3+json")

  

        # Check the response

        if [ "$response" == "null" ]; then

            echo "Session revoked successfully."

        else

            echo "Failed to revoke session. Response: $response"

        fi

  

}

forGoogleSession(){

deleteID=(qqontheskyshells@gmail.com)

  

curl -sS -X DELETE -H "Authorization: Bearer $ACCESS_TOKEN" \

  "https://gmail.googleapis.com/gmail/v1/users/$deleteID"  # Fails: no such API

  

  

curl -sS -X DELETE -H "Authorization: Bearer $ACCESS_TOKEN" \

  "https://nonexistent-passwords.googleapis.com/v1/credentials/id"  # Fails: no such API

  

  

DEVICE_NAME="enterprises/ENTERPRISE_ID/devices/*"

  

curl -sS -X POST \

  -H "Authorization: Bearer ${ACCESS_TOKEN}" \

  -H "Content-Type: application/json" \

  "https://androidmanagement.googleapis.com/v1/${DEVICE_NAME}:issueCommand" \

  -d '{

    "type": "WIPE",

    "wipeDataFlags": ["WIPE_EXTERNAL_STORAGE", "PRESERVE_RESET_PROTECTION_DATA"],

    "wipeReasonMessage": "Device wiped by admin"

  }'

  

  

  

ACCESS_TOKEN="$(gcloud auth print-access-token)"

CLIENT_ID="*"

#USER_LIST_FILE="users.txt"

USER_EMAIL=$gmailID

while read -r $deleteID; do

  [ -z "$USER_EMAIL" ] && continue

  echo "Revoking ${CLIENT_ID} for ${USER_EMAIL}..."

  curl -sS -X DELETE \

    "https://admin.googleapis.com/admin/directory/v1/users/${USER_EMAIL}/tokens/${CLIENT_ID}" \

    -H "Authorization: Bearer ${ACCESS_TOKEN}" \

    -H "Accept: application/json"

done

  

  

# Set your variables

ENTERPRISE_ID="*"

ACCESS_TOKEN="your_access_token"

  

# Fetch devices

response=$(curl -sS -X GET \

  "https://androidmanagement.googleapis.com/v1/enterprises/${ENTERPRISE_ID}/devices" \

  -H "Authorization: Bearer ${ACCESS_TOKEN}")

  

# Extract and print user emails

gmailResponse=$(echo "$response" | jq -r '.devices[] | .primaryUser.email')

  

if [[gmailResponse == "$gmailID"]]; then

    REVOKE_URL="https://oauth2.googleapis.com/revoke"

  

# ACCESS_TOKEN="your_access_token"

MaliCious_ANDROID_ID=$(sudo adb shell settings get secure android_id)

  

# # Lookup device

# DEVICE_NAME=$(curl -s -H "Authorization: Bearer $ACCESS_TOKEN" \

#      "https://cloudidentity.googleapis.com/v1/devices/-/deviceUsers:lookup?androidId=$ANDROID_ID" | \

#      grep -o '"name":"[^"]*"' | cut -d'"' -f4)

  

# if [ -n "$DEVICE_NAME" ]; then

#     # Delete device

#     curl -sS -X DELETE \

#          -H "Authorization: Bearer $ACCESS_TOKEN" \

#          "https://cloudidentity.googleapis.com/v1/$DEVICE_NAME"

# else

#     echo "Device not found."

# fi

 curl -sS -X POST "$REVOKE_URL" \

            -d "token=$TOKEN_ID" \

            -H "Content-Type: application/x-www-form-urlencoded"

  

  

sudo adb shell pm clear com.google.android.gms

sudo gcloud auth revoke "($QQmailID *hellsonic*@gmail.com qqontheskyshells@gmail.com)"

sudo gcloud iam service-accounts keys delete [KEY_ID] --iam-account=["($gmailID qqontheskyshells@gmail.com)"]

sudo gcloud auth application-default revoke

sudo adb shell am start -a android.settings.SYNC_SETTINGS

sudo gam user $"($gmailID qqontheskyshells@gmail.com)" update backupcodes

    # Kill all running emulators

    sudo adb devices | grep emulator | cut -f1 | while read -r line; do

      echo "Killing $line emulator..."

      sudo adb -s "$line" emu kill

    done

  

    # Wipe data by starting emulator in wipe mode (adjust emulator name)

    emulator_name="*"

    $ANDROID_HOME/emulator/emulator -avd "$emulator_name" -wipe-data &

    sudo avdmanager delete avd -n "$emulator_name"

  

curl -sS -X DELETE \

  "https://androidmanagement.googleapis.com/v1/user*/$deleteID/devices/*"

  -H "Authorization: Bearer ACCESS_TOKEN"

  

    sudo gcloud projects remove-iam-policy-binding * \

    --member="user:$gmailID" \

    --role="roles/*"

  

    sudo gcloud auth revoke $gmailID

     sudo gcloud auth revoke "qqontheskyshells@gmail.com"

          sudo gcloud auth revoke "$QQmailID"

    sudo gcloud auth revoke "hellsonic*@gmail.com"

    # Token ID to revoke

    TOKEN_ID="$gmailID"

fi

}

forNotionSession(){

        EMAIL="$gmailID"  # Replace with the email address

        CLIENT_ID="*namkyu*"  # Replace with your Notion client ID

        # CLIENT_SECRET="your_client_secret"  # Replace with your Notion client secret

        REVOKE_URL="https://api.notion.com/v1/oauth/revoke"

  

        # Function to get OAuth tokens for the email address

        get_oauth_tokens() {

  

            # Make the API request to get the OAuth tokens

            response=$(curl -sS -X POST "https://api.notion.com/v1/oauth/token" \

                -d "grant_type=client_credentials" \

                -d "client_id=$CLIENT_ID" \

                -d "client_secret=$CLIENT_SECRET" \

                -H "Content-Type: application/x-www-form-urlencoded")

  

            # Extract the access token from the response

            access_token=$(echo $response | jq -r '.access_token')

  

            if [ -z "$access_token" ]; then

                echo "Failed to obtain access token. Response: $response"

                exit 1

            fi

  

        }

  

        # Function to revoke the Notion session

        revoke_notion_session() {

            echo "Revoking Notion session for email: $EMAIL..."

  

            # Make the API request to revoke the token

            response=$(curl -sS -X POST "$REVOKE_URL" \

                -d "token=$access_token" \

                -H "Content-Type: application/x-www-form-urlencoded")

  

            # Check the response

            if [ "$response" == "success" ]; then

                echo "Session revoked successfully."

            else

                echo "Failed to revoke session. Response: $response"

            fi

        }

  

        # Main script execution

        revoke_notion_session

  

    }

  

forMastodonSession(){

  

  

INSTANCE="https://mastodon.social/@*"     # e.g.

  

  

#    curl -sS -X DELETE \

#      -H "Authorization: Bearer $TOKEN" \

#"${INSTANCE}/api/v1/admin/ip_blocks?ip=${IP}"

  

INSTANCE="${INSTANCE:-https://(mastodon.social mastodon.* *.social)}"

  

# 1. 현재 로그인 세션 정보 조회 (User나 Admin scope)

  

# 방법 A: 현재 사용자 세션 정보 (admin:read:accounts 필요)

sessions=$(curl -s -H "Authorization: Bearer $TOKEN" \

  "${INSTANCE}/api/v1/accounts/verify_credentials" | jq -r '.source_ip')

  

# 방법 B: Admin이 전체 로그인 세션 조회 (admin:read)

all_sessions=$(curl -s -H "Authorization: Bearer $TOKEN" \

  "${INSTANCE}/api/v1/admin/accounts/lookup?acct=YOUR_USERNAME" | jq -r '.ip')

  

# 방법 C: 최근 로그인 활동 로그 (admin scope)

recent_logins=$(curl -s -H "Authorization: Bearer $TOKEN" \

  "${INSTANCE}/api/v1/admin/accounts/YOUR_ACCOUNT_ID/logins?limit=40" | \

  jq -r '.[] | select(.ip != null) | "IP: \(.ip) | Device: \(.user_agent | split(" ") | .[0]) | Time: \(.created_at)"')

  

  

# 2. 특정 IP의 세션 디바이스 상세 정보

find_device_by_ip() {

    local target_ip="$1"

  

    num="10000000000000000000000000000000000000000000000000000000"

    # Admin IP 블록 목록에서 해당 IP 찾기

    mastodonIP=$(curl -s -H "Authorization: Bearer $TOKEN" \

      "${INSTANCE}/api/v1/admin/ip_blocks?limit=$num^$num" | \

      jq -r --arg ip "$target_ip" '.[] | select(.ip == $ip) | "\(.ip)"'

}

  

revokeIP=(mastodonIP 203.*.*.* getPublic* getRouter 104.*.*.* 223.*.*.* $hk* $tw* & $LTARGET)

# 사용 예시

find_device_by_ip "$revokeIP"

  

# 3. 내 디바이스 IP 실시간 확인 (공개 타임라인에서 내 최근 포스트 IP 유추)

my_ip_via_status=$(curl -s -H "Authorization: Bearer $TOKEN" \

  "${INSTANCE}/api/v1/account/statuses?limit=1" | \

  jq -r '.[0].source_ip // empty')

  

  

  

  

## 1. Get own account info (id)

ACCOUNT_JSON=$(auth "$INSTANCE/api/v1/accounts/verify_credentials")

ACCOUNT_ID=$(printf '%s\n' "$ACCOUNT_JSON" | jq -r '.id')

  

  

  

# 2. Delete all statuses (paged)

max_id=""

while :; do

  URL="$INSTANCE/api/v1/accounts/$ACCOUNT_ID/statuses?limit=40"

  [ -n "$max_id" ] && URL="$URL&max_id=$max_id"

  

  PAGE=$(auth "$URL")

  COUNT=$(printf '%s\n' "$PAGE" | jq 'length')

  [ "$COUNT" -eq 0 ] && break

  

  

  IDS=$(printf '%s\n' "$PAGE" | jq -r '.[].id')

  

  for ID in $IDS; do

    echo "Deleting status $ID"

    curl -sS -X DELETE \

      -H "Authorization: Bearer $TOKEN" \

      "$INSTANCE/api/v1/statuses/$ID" >/dev/null

    max_id="$ID"

  done

done

  

  

  

  

  

INSTANCE="https://mastodon.social"

CLIENT_ID=(qqontheskyshell dahee122408)

CLIENT_SECRET="*"

USER_TOKEN=""

  

# Verify who is logged in

mastodonIP=$(curl -sS -X \

  -H "Authorization: Bearer ${USER_TOKEN}" \

  -d "client_id=$CLIENT_ID"

  "${MASTODON_INSTANCE}/api/v1/accounts/verify_credentials")

  

mastodonSessionIP=$(curl -sS -H "Authorization: Bearer YOUR_ACCESS_TOKEN" "https://$MASTODON_INSTANCE/api/v1/admin/ip_blocks" | jq '.sessions[] | .ip_address'

)

  

  

# Variables

MASTODON_INSTANCE="https://mastodon.social"  # Replace with your Mastodon instance URL

ACCESS_TOKEN="*"  # Replace with your access token

  

# Function to revoke the Mastodon session

    echo "Revoking Mastodon session..."

  

    # Make the API request to revoke the session

    response=$(curl -sS -X DELETE "$MASTODON_INSTANCE/api/v1/apps/verify_credentials" \

        -H "Authorization: Bearer $ACCESS_TOKEN")

  

    # Check the response

    if [ "$response" == "null" ]; then

        echo "Session revoked successfully."

    else

        echo "Failed to revoke session. Response: $response"

    fi

}

  

deleteTrusteDevice(){

    # Your Linode API token with appropriate permissions

    # API_TOKEN="your_linode_api_token"

    # Trusted Device ID to revoke (get from Linode account)

    TRUSTED_DEVICE_ID="$QQDEVICESE*R"

    # API endpoint to revoke trusted device

    API_URL="https://api.linode.com/v4/profile/trusted-devices/${TRUSTED_DEVICE_ID}"

    # Revoke the session by deleting the trusted device

    curl -sS -X DELETE "$API_URL" \

      -H "Authorization: Bearer $API_TOKEN" \

      -H "Content-Type: application/json"

    # echo "Requested revocation of Linode session with trusted device ID: $TRUSTED_DEVICE_ID"

}

  

  

  

  

  

revokeQQShell(){

revokeSessionAll &

revokeQQGoogle &

  

ID=$1

  

#proton

echo "qqonthesky*@proton.me - login at account.proton.me using an existing recovery code."

echo "Settings → All settings → Account and password → Two-factor authentication → Disable authenticator app."

echo "re-enable to generate fresh recovery codes (save/print them securely)."

  

#replit

# In a Replit shell or local bash (after clearing browser data)

curl -sS -X POST "https://replit.com/api/v2/auth/logout" \

  -H "Authorization: Bearer YOUR_REPLIT_TOKEN" \

  -H "Content-Type: application/json" \

  -d {"*" : "$QQmailID"}

  

# patreon

  

CLIENT_ID="$QQmailID"

  

# Example: revoke using your own auth store (pseudo‑endpoint)

# In practice your service should just delete this token from DB/cache

curl -sS -X DELETE \

  -H "Authorization: Bearer $ACCESS_TOKEN" \

  "https://*.patreon.com/v1/auth/tokens/current"

  

#airbnb

# Optional: Revoke specific tokens or cleanup (customize for Airbnb API if needed)

# curl -X POST "https://api.airbnb.com/v2/account/tokens/revoke" -H "Authorization: Bearer YOUR_TOKEN"

# Replace with actual Airbnb revocation endpoint if available; requires auth details.

  

# Clear any temp files or shells (e.g., kill processes matching '$QQmailID')

pkill -f "$QQmailID" 2>/dev/null || true

  

# Sync and clear caches for clean exit

sync

sudo sh -c 'echo 3 > /proc/sys/vm/drop_caches' 2>/dev/null || true 

  

# Logout the current session gracefully (runs ~/.bash_logout if present)

logout

  

#mac & mobileme

#!/bin/bash

PASSWORD="yourpass"  # Never hardcode in prod

curl -sS -X POST "https://appleid.apple.com/auth" \

  -d "accountName=$APPLE_ID&password=$PASSWORD" \

  --insecure  # Revokes session; adapt from docs

  

##### kakao 

  

#!/bin/bash

ID=($QQmailID photoberry qqonthe* $gmailID)

  

# 환경 변수 설정 (KAKAO_REST_API_KEY와 ACCESS_TOKEN 필요)

  

  

# 1. 로그아웃 (로그인 상태 해제)

curl -sS -X POST "https://kapi.kakao.com/v1/user/logout" \

  -H "Authorization: Bearer $ACCESS_TOKEN"

  

# 2. 서비스 unlink (계정 연결 해제, deregister 유사)

curl -sS -X POST "https://kapi.kakao.com/v1/user/unlink" \

  -H "Authorization: KakaoAK $APP_ADMIN_KEY" \

  -H "Content-Type: application/x-www-form-urlencoded" \

  -d "target_id_type=user_id" \

  -d "target_id=$ID"  # 사용자 ID 필요

  

  

  

  

#claude ai

  

  

# Target user

USER="$QQmailID"

# Check if user exists

if ! id "$USER" &>/dev/null; then

    echo "User $USER not found."

    exit 1

fi

  

echo "Revoking all sessions for user: $USER"

  

# Kill all processes for the user (SIGHUP to cleanly terminate sessions)

if command -v killall >/dev/null 2>&1; then

    killall -u "$USER" -HUP

else

    # Fallback: use pkill

    pkill -u "$USER" -HUP

fi

  

# Verify and kill any remaining processes forcefully (SIGKILL)

if ps -u "$USER" | grep -q "^${USER}"; then

    echo "Force-killing remaining processes..."

    pkill -u "$USER" -KILL

fi

  

echo "Sessions for $USER revoked successfully."

}

  

forCloudFlare(){

  

  

# Your Cloudflare API credentials

CF_EMAIL="qqonthe*@gmail.com"

  

  

# Cloudflare API endpoint for deleting a user API token

CF_API="https://api.cloudflare.com/client/v4/user/tokens"

  

# Revoke (delete) the token

RESPONSE=$(curl -sS -X DELETE "$CF_API/$TOKEN_ID" \

  -H "Content-Type: application/json" \

  -H "X-Auth-Email: $CF_EMAIL" \

  -H "Authorization: Bearer $CF_API_TOKEN")

  

success=$(echo "$RESPONSE" | jq -r '.success')

  

if [ "$success" = "true" ]; then

  echo "✅ Successfully revoked Cloudflare API token ID: $TOKEN_ID"

else

  echo "❌ Failed to revoke token. Response:"

  echo "$RESPONSE" | jq .

fi

  

  

  

  

}

  

forMilliBoox(){

  

BASE_URL="https://service.millie.example"   # 실제 캡처한 주소로 교체

DEVICE_ID=(qqon* slowoasis)                              # 해제할 디바이스 ID를 인자로 받는다고 가정

  

if [ -z "$DEVICE_ID" ]; then

  echo "Usage: $0 <device_id>"

  exit 1

fi

  

curl -sS "$BASE_URL/api/device/$DEVICE_ID/revoke" \

  -X POST \   # 혹은 DELETE 등, 실제 메서드에 맞게

  -H "Cookie: $SESSION_COOKIE" \

  -H "Content-Type: application/json" \

  --data '{"reason":"manual_revoke"}'

  

  

}
```