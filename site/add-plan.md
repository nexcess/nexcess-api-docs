Portal: Sites
----------------------

**work in progress**

service[site]:add
=================

Orders a new Site Service and creates it first Site.

Add requests are queued, meaning they will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/site/plan

**Access**: service edit permissions

**Parameters**:
@todo

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/site" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{ "app_id": 123, "cloud_id": 45, "domain": "site.example.com", "install_app": true, "package_id": 678 }'
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

{ "id": 12, "identity": "service[site]:add (pending)" }
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
