# Portal: Site

## site:delete-stencil
Deletes a Stencil.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
service edit

#### Input
- int `account_id` (optional): System ID of the Site that the stencil belongs to.

#### Request
```
$ curl -X DELETE "$PORTAL_API_URL/v1/site/{account_id}/stencil/{id}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Tue, 02 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/site/1002/stencil/1234
NocWorx-Api-Version: 0.0.0

{
  "id": 492,
  "identity": "stencil:delete (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/067bdf4c-eaa8-4c5f-80d6-47b4c423079d"
  },
  "status": "pending",
  "action": "stencil:delete",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1637847575,
  "resolved_date": null,
  "resource": null,
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Alice Bowman - alice@example.com",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  },
  "uuid": "067bdf4c-eaa8-4c5f-80d6-47b4c423079d"
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
