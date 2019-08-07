Portal: Cloud Servers
---------------------

**since** 0.0.0

cloud-server:list
=================

Lists a client's cloud servers.

**Endpoint**:  GET /v1/cloud-server

**Access**: service view permission

**Parameters**:
- string[] `filter[...]`: Optional: _available filters TBD._
- integer `page`: Optional: 1-based result set count for paginated results.
- integer `pageSize`: Optional: maximum number of results to include per "page" of a paginated list.
- string `sortBy`: Optional: field to sort the list by; _sortable fields TBD._
- string `sortOrder`: Optional: sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$PORTAL_API_URL/v1/cloud-server" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 17 Jul 2019 01:50:28 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 1656
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.15
Content-Range: items 1-5/5
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

[
  {
    "id": 1077,
    "identity": "cloud.example.com - 203.113.0.1",
    "cloud": { "id": 12345, "identity": "us-midwest-1" },
    "client": { "id": 23456, "identity": "Example, Inc." },
    "has_console": true,
    "network": {
      "public_ip": "203.113.0.1",
      "nat_ip": "10.100.0.1",
      "private_ip": "10.200.0.1"
    },
    "os": { "id": 3456, "identity": "centos 7 (x86_64)" },
    "package": { "id": 45678, "identity": "nx.small" },
    "power_status": "on",
    "service": { "id": 73456, "identity": "cloud.example.com - 203.113.0.1" }
  },

  . . .

]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
