Portal: Service
---------------

**since** 0.5.0

service:resize
==============

Resizes an existing Service to use another Package.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/service/{id}/resize

**Access**: service edit permissions

**Parameters**:
- integer `package_id` (required): system id of the Package to resize to

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/service/$SERVICE_ID/resize" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{ "package_id": '"$NEW_PACKAGE_ID"' }'
```

**Success Response**: 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Tue, 16 Jul 2019 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
X-Powered-By: PHP/7.2.15
Location: /v1/task/3b93d577-41ee-4077-913f-d36f91819bb9
NocWorx-Api-Version: 0.4.0
Served-By: nwdev-web01-int

{ "id": 12, "identity": "service:resize (pending)" }
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (service not found on client account): 404 Not Found

**Failure Response** (invalid inputs): 422 Unprocessable Entity
