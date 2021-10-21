# Portal: Address

## address:list
List Addresses.

#### Access
address view

#### Input
- integer `filter[id]` (optional): filter list by system ID
- integer `match` (optional): match against id value
- integer `range` (optional): find id values within .. range
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): sort list by id.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/address" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 19 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/address
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 73394,
    "identity": "Nexcess Staff",
    "address1": "21700 Melrose Ave",
    "address2": "",
    "city": "Southfield",
    "country": "US",
    "metadata": {
      "scope": "address",
      "uri": "/v1/address/73394"
    },
    "state": "MI",
    "type": "default",
    "zip": "48075"
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
