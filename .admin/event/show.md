Admin: Event
------------

event:show
==========

Shows details of an event.

**Endpoint**:  GET /v1/event/{id}

**Access**: event view permission

**Parameters**:
none.

**Request**:
```
curl -i "$ADMIN_API_URL/v1/event/$EVENT_ID" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 16 Jan 2020 02:59:56 GMT
Content-Type: application/json
Content-Length: 11699
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.21
Content-Range: items 1-22/22
NocWorx-Api-Version: 0.3.0
Served-By: nwdev-web01-int

{
  "id": 12345,
  "identity": "service:store-add - n5s.large - 0.0.0.0/24 - 08/07/2017 10:55:14",
  "metadata": { "scope": "event", "uri": "/v1/event/12345" },
  "scope": "service",
  "action": "store-add",
  "user": {
    "id": 23456,
    "identity": "staff@nexcess.net",
    "metadata": { "scope": "user", "uri": null }
  },
  "client_user": {
    "id": 34567,
    "identity": "user@example.com",
    "metadata": { "scope": "client-user", "uri": null }
  },
  "client": {
    "id": 45678,
    "identity": "Example, LLC",
    "metadata": { "scope": "client-user", "uri": "/v1/client/45678" }
  },
  "ip": "203.0.113.1",
  "resource": {
    "id": 56789,
    "identity": "n5s.large - 0.0.0.0/24",
    "metadata": { "scope": "service", "uri": "/v1/service/56789" }
  },
  "priority": "info",
  "changes": [
    { "property": "service_id", "old_value": null, "new_value": 56789 },
    . . .
  ]
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (does not exist): 404 Not Found
