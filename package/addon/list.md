Portal: Package Addon
---------------------

**since** 0.0.0

package-addon:list
==================

Lists package addons (typically, belonging to a particular package). 
Only addons that can be purchased by the client making the request will be returned.

**Endpoint**:  GET /v1/package/addon

**Alternate Endpoint**:  GET /v1/package/{id}/addon[/{type}]

This alternate endpoint is sugar for `GET /v1/package/addon?filter[package_id]={id}&filter[type]={type}` and will serve identical responses. The `type` parameter is optional.

**Alternate Endpoint**:  GET /v1/package/addon/{type}

This alternate endpoint is sugar for `GET /v1/package/addon?filter[type]={type}` and will serve identical responses.

**Access**: order view permission

**Parameters**:
- string `filter[package_id]` (optional): filters results by package
- string `filter[type]` (optional): filters results by type
- string `filter[name]` (optional): filters results by name
- integer `page` (optional): 1-based result set count for paginated results
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list
- string `sortBy` (optional): field to sort the list by; one of `id`|`name`|`monthly_fee`
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`

**Request**:
```
curl -i "$PORTAL_API_URL/v1/package/$PACKAGE_ID/addon" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 03 Sep 2019 12:54:58 GMT
Content-Type: application/json
Content-Length: 449
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
Content-Range: items 1-4/4
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

[
  { 
    "id": 514,
    "identity": "Standard EV SSL",
    "monthly_fee": "0.00",
    "name": "Standard EV SSL",
    "type": "ssl"
  },
  
  . . .
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
