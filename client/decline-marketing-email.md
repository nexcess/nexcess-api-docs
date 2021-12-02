# Portal: Client

## client:decline-marketing-email
Decline marketing emails for this Client.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
client edit

#### Input
none

#### Request
```
$ curl -i -X DELETE "$PORTAL_API_URL/v1/client/marketing" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Mon, 19 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/client/marketing
NocWorx-Api-Version: 0.0.0

{
  "id": 474,
  "identity": "client:decline-marketing (pending)",
  "status": "pending",
  "action": "client:decline-marketing",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/a30b36fc-f5c4-4982-a426-6a4588581dd8"
  },
  "request_date": 1636720630,
  "resolved_date": null,
  "resource": null,
  "staff_user": null,
  "user": {
  "id": 61420,
  "identity": "Nexcess Staff - support@nexcess.net",
  "metadata": {
    "scope": "user",
    "uri": "/v1/user/61420"
   }
  },
  "uuid": "a30b36fc-f5c4-4982-a426-6a4588581dd8"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
