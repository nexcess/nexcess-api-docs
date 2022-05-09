# Portal: CreditCard

## creditcard:edit
Edit a Credit card details

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
credit card view

#### Input
- string `name` (optional): Nickname for the creditcard.

#### Request
```
$ curl -X POST "$PORTAL_API/v1/creditcard/{id}" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{"name": "My card name"}'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Tue, 28 Dec 2021 12:38:35 GMT
Content-Type: application/json
Content-Length: 597
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 192,
  "identity": "creditcard:edit (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/5916e9c6-b378-4155-aa70-a8ce589f7621"
  },
  "status": "pending",
  "action": "creditcard:edit",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1640695114,
  "resolved_date": null,
  "resource": {
    "id": 39548,
    "identity": "Visa ************1111",
    "metadata": {
      "scope": "creditcard",
      "uri": "/v1/creditcard/39548"
    },
    "type": "Visa"
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
  "uuid": "5916e9c6-b378-4155-aa70-a8ce589f7621"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
