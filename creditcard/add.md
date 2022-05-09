# Portal: CreditCard

## creditcard:add
Creates a new Credit card

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
credit card view

#### Input
- string `cvv` (required): Creditcard's CVV number (security code)
- string `number` (required): Creditcard number
- integer `expiration` (required): Creditcard's expiration date (as a unix timestamp).
- bool `make_primary` (optional): Set this as your primary Creditcard
- string `name` (optional): Nickname for the creditcard.

#### Request
```
$ curl -X POST "$PORTAL_API/v1/creditcard" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{"cvv" :  "504", "expiration" :  1672230798, "number": "4242424242424242"}'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Tue, 28 Dec 2021 12:34:03 GMT
Content-Type: application/json
Content-Length: 475
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 191,
  "identity": "creditcard:add (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/dca50ce3-4993-4b9d-a439-56bf9573b224"
  },
  "status": "pending",
  "action": "creditcard:add",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1640694842,
  "resolved_date": null,
  "resource": null,
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Nexcess Staff - nocworx-dev@nexcess.net",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  },
  "uuid": "dca50ce3-4993-4b9d-a439-56bf9573b224"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
