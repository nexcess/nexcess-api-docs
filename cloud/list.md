Portal: Cloud
-------------

**since** 0.0.0

cloud:list
==========

Lists available cloud hosting installations.

**Endpoint**:  GET /v1/cloud

**Access**: order view permission

**Parameters**:
- string `filter[location]` (optional): filters results by (human-readable) cloud location.
- string `filter[location_code]` (optional): filters results by cloud location code.
- string `filter[country]` (optional): filters results by country.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`location`|`location_code`|`country`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$PORTAL_API_URL/v1/cloud" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 17 Jul 2019 03:45:36 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 147
X-Powered-By: PHP/7.2.15
Content-Range: items 1-1/1
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

[
  {
    "id": 1,
    "identity": "us-midwest-1",
    "type": "openstack",
    "status": "active",
    "location": "Southfield, MI",
    "location_code": "us-midwest-1",
    "country": "US"
  }
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
