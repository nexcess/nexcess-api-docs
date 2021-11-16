# Portal: Client

## client:tax-exempt
Set tax exempt info on client account.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
client edit

#### Input
- string `number` (required): number to set the tax exempt
- array `document_ids` (optional): system ID from the list of document ids

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/client/tax-exempt" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "number" : "X1234567890",
    "document_ids": [23,24]
  }'
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
   "id": 469,
    "identity": "client:set-tax-exempt (pending)",
    "status": "pending",
    "action": "client:set-tax-exempt",
    "api_version": "0.5.0",
    "errors": {},
    "input": {},
    "metadata": {
        "scope": "api-task",
        "uri": "/v1/task/992b4d59-2560-4b6b-9d08-3c763c5a6189"
    },
    "request_date": 1636640504,
    "resolved_date": null,
    "resource": {
        "id": 12345,
        "identity": "Nexcess Staff",
        "status": "active",
        "metadata": {
            "scope": "client",
            "uri": null
        }
    },
    "staff_user": null,
    "user": {
        "id": 12345,
        "identity": "Nexcess Staff - support@nexcess.net",
        "metadata": {
            "scope": "user",
            "uri": "/v1/user/12345"
        }
    },
    "uuid": "992b4d59-2560-4b6b-9d08-3c763c5a6189" 
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
