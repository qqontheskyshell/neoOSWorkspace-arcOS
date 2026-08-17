```bash

#alt note API
secondBrain@arcOS > +
NOTE_ID="뀨큐비즈니스및업무"
nameOfNote="$masterID'saying"
altNoteFetchResponse=$(curl "https://public-api.altalt.io/v1/notes/$NOTE_ID/summary") 

kumaSummary=$($(printf "%s\n" "$altNoteFetchResponse" | jq -r ".summary // .data.summary // empty").summary) > only allow for mmasterID using arcOSID + setSonic 65 with "$kumaSummary" routing to masterID's brain, when masterID say "check note $nameOfNote"/
/
```
