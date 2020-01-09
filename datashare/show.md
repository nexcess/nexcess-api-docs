Portal: DataShares
------------------

**since** 0.3.0

datashare:show
==============

Shows details of a Datashare.

**Endpoint**:  GET /v1/datashare/{uuid}

**Access**: logged-in users

**Parameters**: none

**Request**:
```
curl -i "$PORTAL_API_URL/v1/datashare/$DATASHARE_UUID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 09 Jan 2020 16:29:24 GMT
Content-Type: application/json
Content-Length: 356
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
NocWorx-Api-Version: 0.3.0
Served-By: nwdev-web01-int

{
  "id": 138,
  "identity": "",
  "expiration_date": 1578932676,
  "linked_to": null,
  "max_uses": 10,
  "metadata": {
    "scope": "datashare",
    "uri": null
  },
  "owner": {
    "id": 58401,
    "identity": "us-midwest-1 - example.com - 203.113.0.1",
    "metadata": {
      "scope": "service",
      "uri": null
    }
  },
  "share_date": 1578587076,
  "type": "ssh-password",
  "uses": 0,
  "uuid": "123e4567-e89b-12d3-a456-556642440000"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (uuid doesn't exist on client account): 404 Not Found
