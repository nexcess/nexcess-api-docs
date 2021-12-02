# Portal: Client

## client:accept-marketing-email
Marketing email for client.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
client edit

#### Input
none

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/client/marketing" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Mon, 18 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

{
  "id": 475,
  "identity": "client:accept-marketing (pending)",
  "status": "pending",
  "action": "client:accept-marketing",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/7f6375ec-a99b-4aba-8c53-36ca2c57be90"
  },
  "request_date": 1636722587,
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
  "uuid": "7f6375ec-a99b-4aba-8c53-36ca2c57be90"
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
