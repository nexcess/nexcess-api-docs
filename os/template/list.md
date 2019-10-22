Portal: Os Template
-------------------

**since** 0.2.0

os-template:list
================

Lists operating system installation templates available for cloud servers.

**Endpoint**:  GET /v1/os-template

**Access**: order view permission

**Parameters**:
- string `filter[name]` (optional): filters results by template name.
- string `filter[os]` (optional): filters results by os name.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `type`|`id`|`name`|`version`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$PORTAL_API_URL/v1/os-template" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 22 Oct 2019 12:54:10 GMT
Content-Type: application/json
Content-Length: 457
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
Content-Range: items 1-7/7
NocWorx-Api-Version: 0.1.0
Served-By: nwdev-web01-int

[
  {
    "id": 4,
    "identity": "CentOS 7 x64",
    "uri": "/v1/os-template/4/"
  },

  . . .
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
