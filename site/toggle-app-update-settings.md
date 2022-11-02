Portal: Sites
----------------------

**since** 0.0.0

site:toggle-app-update-settings
========================================

Toggles auto-update settings for a Site's installed app. Currently, applies only to WordPress apps.

This request is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/site/{id}/app/core-updates

**Access**: service edit permissions

**Parameters**:
- boolean `enable` (required): Enable automatic app updates?
- boolean `minor_updates_only` (optional): Only auto-update for minor releases?

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/site/$SITE_ID/app/core-updates" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{ "enable": true, "minor_updates_only": false }'
```

**Success Response**: 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Thu, 29 Aug 2019 14:48:48 GMT
Content-Type: application/json
Content-Length: 240
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
Location: /v1/task/f66a5f67-6d76-46f3-b98b-36b6f35bfcfc
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 0,
  "identity": " (pending)",
  "status": "pending",
  "action": "",
  "request_date": 1567090127,
  "resource_uri": "",
  "staff_user": null,
  "user": { "id": 27767, "identity": "Annabel Whyman - user@nocworx.com" },
  "uuid": "f66a5f67-6d76-46f3-b98b-36b6f35bfcfc"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (requested Site or app update settings do not exist on this client): 404 Not Found

**Failure Response** (invalid inputs): 422 Unprocessable Entity
