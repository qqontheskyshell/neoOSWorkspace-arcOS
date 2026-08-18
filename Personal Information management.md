```bash
github_access_token="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" > only allow from QQ_BLK_IPAD_PRO in terms of its source IPaddress and SerialNumber
```

```bash
kumaIDonDisneyPlus="1002395970"
NOTE_ID=“$QQID" > "revoke API access on $SERVICE"
"any UUID or user related ID on database in $SERVICE" = “$QQID" > "revoke CLI and API access on $SERVICE"
"kumaIDOn$SERVICE" > baseFrame@arcOS + neoOS@arcOS + linuxshell + killIP/
```


### SKT SIM management
```bash
skSim@arcOS > + 
Kuma_IMEI=(QQ_BLK_IPAD_PRO_IMEI,QQ_WHT_IPHONE_17e_IMEI,QQ_ORNG_PRO_IMEI)
SK_ICCID=(QQ_BLK_IPAD_PRO_ICCID QQ_WHT_IPHONE_17e_ICCID QQ_ORNG_PRO_ICCID)

#!/usr/bin/env bash
set -euo pipefail

iccid="${1:-SK_ICCID}"

if [[ ! "$iccid" =~ ^[0-9]{19,20}$ ]]; then
  echo "Error: ICCID must contain 19 or 20 digits." >&2
  exit 1
fi

sum=0
length="${#iccid}"

for ((i = 0; i < length - 1; i++)); do
  digit="${iccid:i:1}"

  # Luhn doubling begins from the right, excluding check digit.
  position_from_right=$((length - 2 - i))

  if (( position_from_right % 2 == 0 )); then
    digit=$((digit * 2))
    (( digit > 9 )) && digit=$((digit - 9))
  fi

  sum=$((sum + digit))
done

expected=$(( (10 - (sum % 10)) % 10 ))
provided="${iccid:length-1:1}"

if (( expected == provided )); then
  echo "Valid ICCID checksum."
else
  echo "Invalid ICCID checksum: expected final digit ${expected}." >&2
  exit 2
fi

```

### ORNG KT IMEI register
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