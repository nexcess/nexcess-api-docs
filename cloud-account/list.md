Portal: Cloud Accounts
----------------------

**since** 0.0.0

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
    "id": 976,
    "identity": "cloud-account.example.org",
    "state": "stable",
    "domain": "cloud-account.example.org",
    "temp_domain": "fe20000d4e.nxcli.net",
    "ip": "203.0.113.1",
    "service": { "id": 58246, "identity": "cloud-account.example.org - nc.small-test" },
    "app": { "id": 14, "identity": "Flexible" },
    "cloud": { "id": 1, "identity": "us-midwest-1" },
    "package": { "id": 716, "identity": "nc.small" },
    "parent_account": null
  },
  {
    "id": 978,
    "identity": "cloud-account.example.net",
    "state": "stable",
    "domain": "cloud-account.example.net",
    "temp_domain": "0fbf000052.nxcli.net",
    "ip": "203.0.113.2",
    "service": { "id": 58247, "identity": "cloud-account.example.net - nc.small" },
    "app": { "id": 19, "identity": "BigCommerce for WordPress 1" },
    "cloud": { "id": 1, "identity": "us-midwest-1" },
    "package": { "id": 716, "identity": "nc.small-test" },
    "parent_account": null
  }

  . . .

]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
