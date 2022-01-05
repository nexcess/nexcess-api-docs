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
  "id": 210,
  "identity": "",
  "metadata": {
    "scope": "datashare",
    "uri": "/v1/datashare/268bdfa5-043a-41ea-b865-6087a1206fb6"
  },
  "expiration_date": 1641725936,
  "linked": {
    "id": 28,
    "identity": "Test Ticket Correct update7 (open)",
    "metadata": {
      "scope": "sf-ticket",
      "uri": "/v1/ticket/07770483"
    },
    "status": "open"
  },
  "max_uses": 10,
  "owner": {
    "id": 38116,
    "identity": "Howell Inc",
    "metadata": {
      "scope": "client",
      "uri": null
    },
    "status": "active"
  },
  "share_date": 1641380336,
  "type": "client-secret",
  "uses": 0,
  "uuid": "268bdfa5-043a-41ea-b865-6087a1206fb6"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (uuid doesn't exist on client account): 404 Not Found
