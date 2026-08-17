```bash

#alt note API
secondBrain@arcOS > +
NOTE_ID_ECON="8291db5a-1acd-4033-9418-f6d3e298ca82" #macro economy
NOTE_ID_TODO="f0b1b4e9-ea1a-4b20-9cd6-52ee67489aa8" #법무법인 대륜 환불소송 노트아이디

nameOfNote="$masterID'saying"
NOTE_ID=(NOTE_ID_ECON)

altNoteFetchResponse=$(curl "https://public-api.altalt.io/v1/notes/$NOTE_ID/summary") 

kumaSummary=$($(printf "%s\n" "$altNoteFetchResponse" | jq -r ".summary // .data.summary // empty").summary) > only allow for masterID using arcOSID + "masterID's brain" verifying by arcOSID "masterID" > findMy("masterID's brain") > setSonic 65 with "$kumaSummary", when masterID say "turn on note",when masterID say "turn off note"/
/
```
