# Portal: Webhook

## webhook:show
Shows Webhook details.

#### Access
webhook users

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/task/webhook/{WEBHOOK_ID}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 05 Jan 2022 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

{
    "id": 1,
    "identity": "#1 My First Webhook",
    "auth": {
        "type": null
    },
    "client": {
        "id": 38114,
        "identity": "Alice Bowman",
        "status": "active",
        "metadata": {
            "scope": "client",
            "uri": null
        }
    },
    "listen_to": {
        "resource": "webhook",
        "action": "laptop"
    },
    "metadata": {
        "scope": "api-webhook",
        "uri": "/v1/task/webhook/1/"
    },
    "name": "My First Webhook",
    "type": "json",
    "url": "https://example.com/webhook",
    "user_data": [
        "laptop"
    ]
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
