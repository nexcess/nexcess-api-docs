# Portal: Affiliate

## affiliate:list-links
Lists Affiliate Links.

#### Access
affiliate links view

#### Input
- integer `filter[id]` (optional): filter list by system ID.
- string `filter[name]` (optional): filter list by name.
- string `filter[target_url]` (optional): filter list by target url.
- string `filter[status]` (optional): filter list by status.
- integer `match[id]` (optional): match against system ID.
- string `match[name]` (optional): match against affiliate link name.
- string `match[target_url]` (optional): match against target url.
- string `match[status]` (optional): match against status value.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`name`|`target_url`|`status`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/affiliate/link" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Fri, 05 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "name": "Magento Hosting",
    "target_url": "http://www.nexcess.net/magento-hosting"
    "status": "active"
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
