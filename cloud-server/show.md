Portal: Cloud Servers
---------------------

**since** 0.0.0

cloud-server:show
==================

Shows details of a cloud server.

**Endpoint**:  GET /v1/cloud-server/{id}

**Access**: service view permission

**Parameters**: none

**Request**:
```
curl -i "$PORTAL_API_URL/v1/cloud-server/$CLOUDSERVER_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
