# Portal: Client

## client:change-pin
Changes the client account's call-in PIN number.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
client edit

#### Input
- string `pin` (optional): pin; six-digit client pin code to set.

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/client/pin" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "pin":"123456"
  }'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Mon, 15 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/client/pin
NocWorx-Api-Version: 0.0.0

{
  "id": 480,
  "identity": "client:change-pin (pending)",
  "status": "pending",
  "action": "client:change-pin",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/dffc30a3-b16a-4fe3-9234-48722dbd3112"
  },
  "request_date": 1636977191,
  "resolved_date": null,
  "resource": {
    "id": 38114,
    "identity": Example, Inc.",
    "status": "active",
    "metadata": {
      "scope": "client",
      "uri": null
    }
  },
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Nexcess Staff - support@nexcess.net",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  },
  "uuid": "dffc30a3-b16a-4fe3-9234-48722dbd3112"
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity
