# Portal: Api Token

## api-token:delete
Deletes an Api Token.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
logged-in users

#### Input
- int `id` (required): System ID of the Api Token to delete

#### Request
```
$ curl -i -X DELETE "$PORTAL_API_URL/v1/api-token/{id}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Tue, 02 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/api-token/5
NocWorx-Api-Version: 0.0.0

{
  "id": 466,
  "identity": "api-token:delete (pending)",
  "status": "pending",
  "action": "api-token:delete",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/10d1bbc5-a682-4fd6-8b21-1ed5b94e9242"
  },
  "request_date": 1635852710,
  "resolved_date": null,
  "resource": {
    "id": 6,
    "identity": "Example, Inc",
    "metadata": {
      "scope": "client-user-api-token",
      "uri": "/v1/api-token/6"
    }
  },
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Example, Inc - support@nexcess.net",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  },
  "uuid": "10d1bbc5-a682-4fd6-8b21-1ed5b94e9242"
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
