```bash
 
cloudKit@arcOS > +
+BaseConfig@arcOS/
+WDSKit@arcOS/
+Protection@arcOS/
+DeviceKit@arcOS/
+BaseConfig@arcOS + baseFrame@arcOS/ 
+linuxshell/ 
+proot-distro remove rockylinux  proot-distro clear-cache/

cloudKit@arcOS="

SEARCH_NAME="${1:-$QQID}"

ONLY_FOLDERS="${2:-false}"   # true or false

  

Q="name = '${SEARCH_NAME}' and trashed = false"

if [[ "$ONLY_FOLDERS" == "true" ]]; then

  Q="${Q} and mimeType = 'application/vnd.google-apps.folder'"

fi

  

response=$(curl -sS \

  -G "https://www.googleapis.com/drive/v3/files" \

  -H "Authorization: Bearer ${ACCESS_TOKEN}" \

  --data-urlencode "q=${Q}" \

  --data-urlencode "spaces=drive" \

  --data-urlencode "fields=files(id,name,mimeType,parents),nextPageToken" \

  --data-urlencode "pageSize=$num" \

| jq -r '.files[] | [.name, .id, .mimeType, (.parents // [] | join(","))]')

  

response.files.id > frame@arcOS & done

"

```