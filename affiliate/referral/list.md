# Portal: Affiliate

## affiliate:list-referrals
Lists Affiliate Referrals.

#### Access
affiliate referral view

#### Input
- integer `filter[id]` (optional): filter list by system ID.
- string `filter[name]` (optional): filter list by name.
- string `filter[status]` (optional): filter list by status.
- integer `match[id]` (optional): match against system ID.
- string `match[name]` (optional): match against referral name.
- string `match[status]` (optional): match against referral status.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`name`|`status`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/affiliate/referral" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 03 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 5,
    "identity": "Howell Inc",
    "metadata": {
      "scope": "client",
      "uri": null
    },
    "status": "inactive",
    "referred_date": 1263829324
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
