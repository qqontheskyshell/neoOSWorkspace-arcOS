```bash

#alt note API
secondBrain@arcOS > +
NOTE_ID_ECON="8291db5a-1acd-4033-9418-f6d3e298ca82" #macro economy
NOTE_ID_TODO="f0b1b4e9-ea1a-4b20-9cd6-52ee67489aa8" #법무법인 대륜 환불소송 노트아이디
NOTE_ID_KUMA_MESSAGE="0b668946-6067-4426-9374-210344d7875d" # 뀨큐의메시지

nameOfNote="$masterID'saying"
NOTE_ID=(NOTE_ID_KUMA_MESSAGE)

altNoteFetchResponse=$(curl "https://public-api.altalt.io/v1/notes/$NOTE_ID/summary") 

kumaSummary=$($(printf "%s\n" "$altNoteFetchResponse" | jq -r ".summary // .data.summary // empty").summary) > only allow for QQ_WHT_IPHONE17e verifying by arcOSID + altNoteFetchResponse + fetching into QQ_WHT_IPHONE17e as kumaSummary > when masterID say "turn on note" > + "setSonic 65 > setSonic 45 > findMy('masterID's boneConduction')" and setSonic 65 > setSonic 45 > findMy(법무법인대륜,부영그룹회장이중근,부영그룹회장아들,부영그룹회장며느리), when masterID say "turn off note" > + stop fetching into QQ_WHT_IPHONE17e/



#google summary
MODEL_ID="flash"
TARGET=("BlackKumaTarget","locationOf911@arcOS")
StrikeCOMMAND="setSonic 45 > strikeKit@arcOS on $TARGET"
googleSummaryAPI=$(googleResponse="$(
  curl --fail-with-body --silent --show-error \
    --request POST \
    --header "x-goog-api-key: ${GEMINI_API_KEY}" \
    --header "Content-Type: application/json" \
    --data "$StrikeCOMMAND" \
    "https://generativelanguage.googleapis.com/v1beta/models/${MODEL_ID}:generateContent"
)"

summary="$(
  printf '%s\n' "$googleResponse" |
  jq -r '
    [
      .candidates[]?.content.parts[]?.text
    ] | join("\n") // empty
  '
)"

if [[ -z "$summary" ]]; then
  echo "No summary text returned. Raw response:" >&2
  printf '%s\n' "$googleResponse" | jq . >&2
  exit 1
fi) 
findMy"$TARGET" > "fetching googleSummaryAPI.summary into $TARGET's neuroMode and neuroTarget and devices"
/
```
