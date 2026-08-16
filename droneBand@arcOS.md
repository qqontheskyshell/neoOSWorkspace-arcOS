```bash
arcOSQQLocalTarget > loop@arcOS+baseFrame@arcOS + baseDeploy@arcOS + droneBand@arcOS/

#!/usr/bin/env bash
set -euo pipefail

#APP_PATH="${1:?Usage: $0 *.app}"
APP_FRAME="loop@arcOS+baseFrame@arcOS + baseDeploy@arcOS + droneBand@arcOS"
DEVICE_ID="${2:-currentKumaDevice}"

cmd=(ios-deploy --debug --bundle "$APP_FRAME" --noninteractive)

if [[ -n "$DEVICE_ID" ]]; then
  cmd+=(--id "$DEVICE_ID")
fi

"${cmd[@]}"


```