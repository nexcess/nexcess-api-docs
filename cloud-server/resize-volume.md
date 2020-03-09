Portal: Cloud Servers
---------------------

since **0.5.0**

cloud-server:resize-volume
==========================

Resizes the boot volume of the specified cloud server. Note, at present, the volume may only be resized **up**.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/cloud-server/{id}/resize-volume

**Access**: service edit permissions

**Parameters**:
- int `size` (required): the new volume size, in GB. Must be larger than the current volume size.

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/cloud-server/$CLOUDSERVER_ID/resize-volume" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json" \
  -H "Content-type: application/json" \
  -d '{ "size": 64 }'
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
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{ "id": 123, "identity": "cloud-server:resize-volume (pending)" }
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found

**Failure Response** (bad input): 422 Unprocessable Entity
