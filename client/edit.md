# Portal: Client

## client:edit
Edit client information.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
client edit

#### Input
- string `name` (optional): name; must contain a single line of text.
- string `self_classification` (optional): client self classification; one of `blogger`|`business-owner`|`designer`|`developer`|`enterprise-customer`|`freelancer`|`marketer`
- string `purchase_order_number` (optional): Custom purchase order number; must contain a single line of text.
- bool `agency_relation` (optional): Is this Client an Agency?

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/client" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "name":"Howell, Inc.",
    "self_classification":"developer",
    "purchase_order_number":"X1234567890",
    "agency_relation":"true"
  }'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Mon, 15 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/client
NocWorx-Api-Version: 0.0.0

{
    "id": 482,
    "identity": "client:edit (pending)",
    "metadata": {
        "scope": "api-task",
        "uri": "/v1/task/665537fc-f94e-4b5c-9453-5e6e58a01611"
    },
    "status": "pending",
    "action": "client:edit",
    "api_version": "0.5.0",
    "errors": {},
    "input": {},
    "request_date": 1636984344,
    "resolved_date": null,
    "resource": {
        "id": 38114,
        "identity": "Example, Inc.",
        "metadata": {
            "scope": "client",
            "uri": null
        },
        "status": "active"
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
    "uuid": "665537fc-f94e-4b5c-9453-5e6e58a01611"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity
