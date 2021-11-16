# Portal: Cloud Servers

## cloud-server:resize
Resizes the cloud server and associates it with a new service package. Note, at present, disk space is **not resized** along with other resources.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
service edit permissions

#### Input
- int `package_id` (required): the id of the service package to resize to. @see package:list

#### Request:
```
$ curl -X POST "$PORTAL_API/v1/cloud-server/$CLOUDSERVER_ID/resize" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json" \
  -H "Content-type: application/json" \
  -d '{ "package_id": 678 }'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
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

{ "id": 123, "identity": "cloud-server:resize (pending)" }
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
