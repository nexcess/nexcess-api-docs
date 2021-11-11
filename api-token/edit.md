# Portal: Api Token

## api-token:edit
Edits a stored Api Token.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
logged-in users

#### Input
- integer `id` (required): System ID of the Api Token to edit
- string `name` (required): name; must contain a single line of text

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/api-token/$TOKEN_ID \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "name":"workstation"
  }'
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
  "id": 472,
  "identity": "api-token:edit (success)",
  "status": "success",
  "action": "api-token:edit",
  "api_version": "0.5.0",
  "errors": {},
  "input": {
    "id": 8,
    "name": "Neeraja API Token test"
  },
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/add0d0f1-dbc4-4a3b-a6ee-f1f58742196e"
  },
  "request_date": 1636646271,
  "resolved_date": 1636646273,
  "resource": {
    "id": 8,
    "identity": "Example, Inc.",
    "metadata": {
      "scope": "client-user-api-token",
      "uri": "/v1/api-token/8"
    }
  },
  "staff_user": null,
  "user": {
    "id": 12345,
    "identity": "Example, Inc - support@nexcess.net",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/12345"
    }
  },
  "uuid": "add0d0f1-dbc4-4a3b-a6ee-f1f58742196e"
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
