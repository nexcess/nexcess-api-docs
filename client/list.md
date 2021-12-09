# Portal: Client

## client:list
Lists Client accounts that the authenticated user belongs to.

#### Access
logged-in users

#### Input
none

#### Input
- integer `filter[id]` (optional): filter list by system ID
- integer `match[id]` (optional): match against id value
- string `range[id]` (optional): find system IDs within "{min}..{max}" range.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): sort list by id.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl "$PORTAL_API_URL/v1/client" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Thu, 11 Oct 2021 12:51:27 GMT
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 12345,
    "identity": "Bechtelar PLC",
    "status": "active",
    "external_key": "",
    "external_key_prefix": null,
    "is_tax_exempt": false,
    "metadata": {
      "scope": "client",
      "uri": null
    },
    "name": "Bechtelar PLC",
    "owner": {
      "id": 61383,
      "identity": "Alice Bowman - alice@example.com",
      "metadata": {
        "scope": "user",
        "uri": "/v1/user/12345"
      }
    },
    "self_classification": ""
  },
  
  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
