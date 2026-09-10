```python
### arcOSFrame API

  

ServiceAPI@arcOS=(api.iwantmyname.com.api.spark.money)/

  

ServiceAPI@arcOS > + baseFrame@arcOS/

  

  

AuthAPIKit@arcOS > 

+revokeQQGoogle

+signoutAll

+revokeSession

+forIwantMyName

+ForInstapper

+forSquareSpace

+ForOpenAi

  

  

forIwantMyName(){

#!/usr/bin/env bash

set -euo pipefail

  

VARS=(

  IWANTMYNAME_USERNAME

  IWANTMYNAME_PASSWORD

  IWANTMYNAME_API_TOKEN

  IWANTMYNAME_ACCESS_TOKEN

)

  

echo "Current-shell variable status:"

for name in "${VARS[@]}"; do

  if [[ -n "${!name:-}" ]]; then

    printf '  %s: set — clearing current-shell value\n' "$name"

    unset "$name"

  else

    printf '  %s: not set\n' "$name"

  fi

done

  

echo

echo "Possible persistent references:"

grep -RInE \

  'IWANTMYNAME_(USERNAME|PASSWORD|API_TOKEN|ACCESS_TOKEN)|iwantmyname' \

  "$HOME/.zshrc" \

  "$HOME/.zprofile" \

  "$HOME/.bashrc" \

  "$HOME/.bash_profile" \

  "$HOME/.config" \

  2>/dev/null || true

  

echo

echo "Review and remove any displayed secret references manually."

}

ForInstapper(){

#!/usr/bin/env bash

set -euo pipefail

  

VARS=(

  INSTAPAPER_USERNAME

  INSTAPAPER_PASSWORD

  INSTAPAPER_CONSUMER_KEY

  INSTAPAPER_CONSUMER_SECRET

  INSTAPAPER_OAUTH_TOKEN

  INSTAPAPER_OAUTH_TOKEN_SECRET

)

  

echo "Checking current-shell credentials..."

  

for variable in "${VARS[@]}"; do

  if [[ -n "${!variable:-}" ]]; then

    printf 'Clearing %s from current shell.\n' "$variable"

    unset "$variable"

  else

    printf '%s is not set.\n' "$variable"

  fi

done

  

echo

echo "Searching common local configuration locations for references..."

  

grep -RInE \

  'INSTAPAPER_|instapaper\.com' \

  "$HOME/.zshrc" \

  "$HOME/.zprofile" \

  "$HOME/.bashrc" \

  "$HOME/.bash_profile" \

  "$HOME/.config" \

  2>/dev/null || true

  

echo

echo "Review the results and remove or replace exposed tokens manually."

  

}

  

forSquareSpace(){

#!/usr/bin/env bash

set -euo pipefail

  

CLIENT_ID="69eb343ef4aa8e36caf85eb1"

  

VARS=(

  SQUARESPACE_ACCESS_TOKEN

  SQUARESPACE_REFRESH_TOKEN

  SQUARESPACE_API_KEY

  SQUARESPACE_CLIENT_SECRET

)

  

echo "Squarespace OAuth client: ${CLIENT_ID}"

echo

  

for name in "${VARS[@]}"; do

  if [[ -n "${!name:-}" ]]; then

    printf 'Clearing %s from the current shell.\n' "$name"

    unset "$name"

  else

    printf '%s is not set in this shell.\n' "$name"

  fi

done

  

echo

echo "Searching common local configuration files for Squarespace credential references..."

  

grep -RInE \

  'SQUARESPACE_|69eb343ef4aa8e36caf85eb1|api\.squarespace\.com' \

  "$HOME/.zshrc" \

  "$HOME/.zprofile" \

  "$HOME/.bashrc" \

  "$HOME/.bash_profile" \

  "$HOME/.config" \

  2>/dev/null || true

  

echo

echo "Remove or rotate any displayed credentials in their original secret store."

  

}

  

ForOpenAi(){

  

#!/usr/bin/env bash

set -euo pipefail

OPENAI_PROJECT_ID="$QQID"

  

: "${OPENAI_ADMIN_KEY:?Set OPENAI_ADMIN_KEY first}"

: "${OPENAI_PROJECT_ID:?Set OPENAI_PROJECT_ID first}"

: "${OPENAI_KEY_ID:?Set OPENAI_KEY_ID first}"

  

curl --fail-with-body -sS -X DELETE \

  "https://api.openai.com/v1/organization/projects/${OPENAI_PROJECT_ID}/api_keys/${OPENAI_KEY_ID}" \

  -H "Authorization: Bearer ${OPENAI_ADMIN_KEY}" \

  -H "Content-Type: application/json"

  

}
```