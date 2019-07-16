Portal: Cloud Accounts
----------------------

**work in progress**

cloud-account:list
==================

Lists a client's cloud accounts.

**Endpoint**:  GET /v1/cloud-account

**Access**: service view permission

**Parameters**:
- `filter[...]`: Optional: _available filters TBD._
- `page`: Optional: 1-based result set count for paginated results.
- `pageSize`: Optional: maximum number of results to include per "page" of a paginated list.
- `sortBy`: Optional: field to sort the list by; _sortable fields TBD._
- `sortOrder`: Optional: sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$PORTAL_API_URL/v1/cloud-account" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Fri, 12 Jul 2019 17:22:46 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 530
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.15
Content-Range: items 1-9/9
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

[
  {
    "id": 91011,
    "identity": "cloud-account.example.com",
    "domain": "cloud-account.example.com",
    "temp_domain": "fe12c2ad4e.nxcli.net",
    "state": "stable",
    "ip": "203.0.113.1",
    "app": { "id": 123, "identity": "flexible" },
    "location": { "id": 45, "identity": "us-midwest-1" },
    "package": { "id": 678, "identity": "nc.small" },
    "parent_account": null
  },

  . . .

]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
