# Portal: Cloud Servers

## cloud-server:cancel
Requests a Cloud Server and its associated service not be renewed at the conclusion of the current billing cycle.

Cancellation survey questions can vary with time and depending on the type of service. Note the survey is optional: it is intended for use on the client website, where filling out forms interactively is easier. Responses are welcome on the Api, but not required.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
service delete permissions

#### Input
- array `survey[]` (optional): question id:response pairs. @see cloud-server:cancel-survey

#### Request:
```
$ curl -i -X POST "$PORTAL_API_URL/v1/cloud-server/{id}/cancel" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json" \
  -H "Xontent-type: application/json"
  -d '{ 1: [4], 2: "New business", 3: 10, 4: 1, 5: 1 }'
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

{ "id": 12, "identity": "cloud-server:cancel (pending)" }
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
