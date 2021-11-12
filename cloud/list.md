# Portal: Cloud

## cloud:list
List Apps.

#### Access
cloud view

#### Input
- integer `filter[location]` (optional): filter list by cloud location.
- integer `filter[location_code]` (optional): filter list by cloud location code.
- integer `filter[country]` (optional): filter list by country.
- integer `filter[package_id]` (optional): filter list by package ID.
- integer `match[location]` (optional): match against location value.
- integer `match[location_code]` (optional): match against location code value.
- integer `match[country]` (optional): match against country value.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`location`|`location_code`|`country`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/cloud" \
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
    "id": 4,
    "identity": "us-midwest-2",
    "status": "active",
    "country": "US",
    "location": "Lansing, MI",
    "location_code": "us-midwest-2",
    "metadata": {
      "scope": "virt-cloud",
      "uri": null
    },
    "type": "openstack"
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
