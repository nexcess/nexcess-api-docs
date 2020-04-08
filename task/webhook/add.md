Portal: Webhooks
----------------

**since** 0.5.0

webhook:add
===========

Creates a new stored webhook.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/task/webhook

**Access**: account edit permissions

**Parameters**:
- string `name` (required): name for the webhook
- string `url` (required): fully qualified target URL for the webhook (only https is currently supported)
- string `type` (optional): one of `json`(application/json (default))|`form`(application/x-www-urlencoded)|`multipart`(multipart/form-data)
- string `resource` (optional): the api resource the webhook should listen for. `*` means "any resource"; `-` means "none" (disable)
- string `action` (optional): the api action the webhook should listen for. `*` means "any action"; `-` means "none" (disable)
- array `auth` (optional):
  - string `auth[type]` (required): one of `basic`|`digest`|`bearer`
  - string `auth[username]` (required if type=basic|digest): username
  - string `auth[password]` (required if type=basic|digest): password
  - string `auth[token]` (required if type=bearer): bearer token
- array `user_data` (optional): arbitrary user-defined data to be included with the webhook

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/task/webhook" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "name": "example-webhook",
    "url": "https://example.com/webhook",
    "resource": "cloud-server",
    "action": "reboot",
    "auth": {
      "type": "basic",
      "username": "foo",
      "password": "passw0rd!"
    },
    "user_data": { "whatever": "you like" }
  }'
```

**Success Response**: 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Tue, 16 Jul 2019 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
X-Powered-By: PHP/7.4.2
Location: /v1/task/3b93d577-41ee-4077-913f-d36f91819bb9
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{ "id": 12, "identity": "webhook:add (pending)" }
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
