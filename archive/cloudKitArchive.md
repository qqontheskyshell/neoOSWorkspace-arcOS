```markdown
 
  

  

mapKit@arcOS="

  

API_KEY="YOUR_GOOGLE_MAPS_API_KEY"

BASE_URL="https://maps.googleapis.com/maps/api/geocode/json"

  

query="$*"

  

if [ -z "$query" ]; then

  echo "Usage:"

  echo "  ./google_main_location.sh \"Eiffel Tower\""

  echo "  ./google_main_location.sh \"37.4220,-122.0841\""

  exit 1

fi

  

if [[ "$query" =~ ^-?[0-9]+\.[0-9]+,-?[0-9]+\.[0-9]+$ ]]; then

  # Reverse geocoding from coordinates

  response=$(curl -sG "$BASE_URL" \

    --data-urlencode "latlng=$query" \

    --data-urlencode "key=$API_KEY")

else

  # Geocoding from place name or address

  response=$(curl -sG "$BASE_URL" \

    --data-urlencode "address=$query" \

    --data-urlencode "key=$API_KEY")

fi

  

status=$(echo "$response" | jq -r '.status')

if [ "$status" != "OK" ]; then

  echo "Request failed: $status"

  echo "$response" | jq .

  exit 1

fi

  

echo "Main result:"

echo "$response" | jq -r '.results[0] | {

  formatted_address,

  place_id,

  location: .geometry.location,

  location_type: .geometry.location_type,

  result_types: .types

}'

"
```