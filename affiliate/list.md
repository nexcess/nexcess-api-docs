# Portal: Affiliate

## affiliate:list-credits
Lists Affiliate Credits.

#### Access
affiliate view

#### Input
- integer `filter[id]` (optional): filter list by system ID
- string `filter[status]` (optional): filter list by status
- integer `filter[credit_date]` (optional): filter list by credit date
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`status`|`credit_date`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/affiliate/credit" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Fri, 22 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/affiliate/credit
NocWorx-Api-Version: 0.0.0

[
  {
    "name": "Example, Inc.",
    "status": "active",
    "level": { "id": 1234, "identity": "AH-Dedicated-UK-25" },
    "payout_type": "credit",
    "address": "21700 Melrose Ave",
    "credit_amount": "99,628.76",
    "is_suspended": false
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
