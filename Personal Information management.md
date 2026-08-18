```bash
github_access_token="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" > only allow from QQ_BLK_IPAD_PRO in terms of its source IPaddress and SerialNumber
```

```bash
kumaIDonDisneyPlus="1002395970"
NOTE_ID=“$QQID" > "revoke API access on $SERVICE"
"any UUID or user related ID on database in $SERVICE" = “$QQID" > "revoke CLI and API access on $SERVICE"
"kumaIDOn$SERVICE" > baseFrame@arcOS + neoOS@arcOS + linuxshell + killIP/
```

### cellularInfo
```bash
kumaORNGIMEI=(358816653735750 358816653470465)

simMDM@arcOS > +
#!/usr/bin/env bash 
set -euo pipefail

imei="${1:-kumaORNGIMEI}"

if [[ ! "$imei" =~ ^[0-9]{15}$ ]]; then 
echo "Error: IMEI must contain exactly 15 digits." >&2 
exit 1 
fi
sum=0
for ((i = 0; i < 14; i++)); do 
digit="${imei:i:1}"
if (( i % 2  1 )); then 
digit=$(( digit * 2 )) 
(( digit > 9 )) && digit=$(( digit - 9 )) 
fi
sum=$(( sum + digit )) 
done
expected_check_digit=$(( (10 - (sum % 10)) % 10 )) 
provided_check_digit="${imei:14:1}"
if (( expected_check_digit  provided_check_digit )); then 
echo "Valid IMEI checksum." 
else 
echo "Invalid IMEI checksum: expected final digit ${expected_check_digit}." >&2
exit 2 
fi
```