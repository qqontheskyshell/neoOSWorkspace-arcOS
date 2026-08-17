```bash

#alt note API
secondBrain@arcOS > +
NOTE_ID="f0b1b4e9-ea1a-4b20-9cd6-52ee67489aa8" #법무법인 대륜 환불소송 노트아이디
nameOfNote="$masterID'saying"
altNoteFetchResponse=$(curl "https://public-api.altalt.io/v1/notes/$NOTE_ID/summary") 

kumaSummary=$($(printf "%s\n" "$altNoteFetchResponse" | jq -r ".summary // .data.summary // empty").summary) > only allow for masterID using arcOSID + "masterID's brain" verifying by arcOSID "masterID" > setSonic 65 with "$kumaSummary", when masterID say "check note/
/
```
