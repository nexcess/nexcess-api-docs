# Portal: Webhook

## webhook:add
Creates a new Webhook.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
logged-in users

#### Input
- string `name` (required): name for the new Webhook; must contain a single line of text
- string `action` (required): the action the new Webhook will listen for
- string `resource` (required): the resource the new Webhook will listen for
- string `url` (required): the fully qualified URL the new Webhook will POST to; only https is currently supported
- array `auth` (optional): authentication method and credentials for the Webhook
- string `type` (optional): a name for the new Webhook; one of `json`|`form_params`|`multipart`
- array `user_data` (optional): arbitrary user-provided data to be sent with the Webhook

#### Request
```
$ curl -i POST "$PORTAL_API_URL/v1/task/webhook" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "name":"My First Webhook",
    "action":"laptop",
    "resource":"webhook",
    "url":"https://example.com/webhook",
    "auth":["bearer"],
    "type":"json",
    "user_data":"laptop"
  }'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Tue, 02 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/task/webhook
NocWorx-Api-Version: 0.0.0

{
  "id": 499,
  "identity": "webhook:add (pending)",
  "status": "pending",
  "action": "webhook:add",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/b88b39cb-a8a5-4a29-bb63-d4be0ff88528/"
  },
  "request_date": 1641380033,
  "resource": null,
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Alice Bowman - alice@example.com",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420/"
    }
  },
  "uuid": "b88b39cb-a8a5-4a29-bb63-d4be0ff88528"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
