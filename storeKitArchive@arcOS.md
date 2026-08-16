```markdown
arcOSStoreKit=(

grabShell > repeat(arcOSnx & arcOSBaseKit &) &

  

grabShell=(

  

#USERS

GRAB_API_BASE="${GRAB_API_BASE:-https://api.grab.com}"

EMAIL="${1:-*}"

#ENDPOINT="${ENDPOINT:?Set ENDPOINT}"

ENDPOINT="${ENDPOINT:-grab_service_name.loyalty}"

  

  

response="$(curl -sS \

  -H "Authorization: Bearer $TOKEN" \

  -H "Accept: application/json" \

  "${GRAB_API_BASE}${ENDPOINT}?email=${EMAIL}"

)"

  

  

  

      echo "Favorite drivers:"

      favoriteDriverInGrab=$(echo "$response" | jq -r '

        (.favorites.drivers // .data.favouriteDrivers // [])[]?

          | "\(.id)\t\(.name)\t\(.rating // "N/A")"

          ')

  

          echo "Favorite food stores:"

          favoriteFoodStoreInGrab=$(echo "$response" | jq -r '

            (.favorites.stores // .data.favouriteStores // .stores // [])

              | map(select(.isFavorite == true or .favorite == true) // .)[]?

                | "\(.id)\t\(.name)\t\(.category // "unknown")"

                ')

  

  

          favoriteStoreInGrab=$(echo "$response" | jq -r '

            # pick where the orders array lives

              (.orders // .data.orders // [])

                # filter favorite orders (if such a flag exists)

                  | map(select(.isFavorite == true or .favorite == true) // .)

                    # iterate each favorite order

                      | .[]

                        | [

                        (.id // .orderId // "no-id"),

                          (

                            .store.name

                            // .storeName

                            // .merchant.name

                            // "unknown-store"

                          )

                        ]

                     | @tsv

                    '

  

  

Favorite_Grab=(favoriteDriverInGrab favoriteFoodStoreInGrab favoriteStoreInGrab)

Favorite_Grab &

)
```