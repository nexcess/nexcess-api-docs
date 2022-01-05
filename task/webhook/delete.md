# Portal: Webhook

## webhook:delete
Deletes a Webhook.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
webhook edit

#### Input
- int `id` (required): System ID of the Webhook to delete

#### Request
```
$ curl -i DELETE "$PORTAL_API_URL/v1/task/webhook/{webhook_id}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Wed, 05 Jan 2022 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/task/webhook/1234
NocWorx-Api-Version: 0.0.0

{
  "id": 499,
  "identity": "webhook:delete (pending)",
  "status": "pending",
  "action": "webhook:delete",
  "metadata": {
      "scope": "webhook",
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
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
