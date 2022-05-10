Portal: DataShares

datashare:delete
==============
Deletes a datashare.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
datashare delete permissions

#### Input
none

#### Request

```
$ curl -X DELETE "$PORTAL_API/v1/datashare/$UUID" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
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
Location: /v1/task/720c37ff-d968-4f49-965b-906bfe0babc0
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 576,
  "identity": "datashare:delete (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/720c37ff-d968-4f49-965b-906bfe0babc0"
  },
  "status": "pending",
  "action": "datashare:delete",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1641381766,
  "resolved_date": null,
  "resource": {
    "id": 210,
    "identity": "",
    "metadata": {
      "scope": "datashare",
      "uri": "/v1/datashare/268bdfa5-043a-41ea-b865-6087a1206fb6"
    },
    "type": "client-secret"
  },
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Nexcess Staff - nocworx-dev@nexcess.net",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  },
  "uuid": "720c37ff-d968-4f49-965b-906bfe0babc0"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
