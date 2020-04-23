Admin: Webhook
--------------

**since** 0.5.0

webhook:show
============

Shows a stored webhook.

**Endpoint**:  GET /v1/task/webhook/{webhook_id}

**Access**: client view permission

**Parameters**: none

**Request**:
```
curl -i "$ADMIN_API_URL/v1/task/webhook/$WEBHOOK_ID" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 17 Jul 2019 01:50:28 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 1656
Vary: Accept-Encoding
X-Powered-By: PHP/7.4.2
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 14,
  "identity": "#14 example-webhook",
  "auth": {
    "type": "basic",
    "username": "foo",
    "password": "****"
  },
  "client": null,
  "company": {
    "id": 9,
    "identity": "Managed Hosting",
    "metadata": {
      "scope": "company",
      "uri": null
    }
  },
  "listen_to": {
    "resource": "cloud-server",
    "action": "reboot"
  },
  "metadata": {
    "scope": "api-webhook",
    "uri": "/v1/task/webhook/14/"
  },
  "name": "example-webhook",
  "type": "json",
  "url": "https://example.com/webhook",
  "user_data": { "whatever": "you like" }
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
