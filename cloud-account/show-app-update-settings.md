Portal: Cloud Accounts
----------------------

**since** 0.0.0

cloud-account:show-app-update-settings
======================================

Shows auto-update settings for a cloud account's installed app. Currently, applies only to WordPress apps.

**Endpoint**:  GET /v1/cloud-account/{id}/app/core-updates

**Access**: service view permission

**Parameters**: none

**Request**:
```
curl -i "$PORTAL_API_URL/v1/cloud-account/$CLOUDACCOUNT_ID/app/core-updates" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 29 Aug 2019 14:40:37 GMT
Content-Type: application/json
Content-Length: 146
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "cloud_account": { "id": 981, "identity": "wp.example.com" },
  "disabled_date": null,
  "enabled": true,
  "last_updated_date": null,
  "minor_updates_only": false
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (requested cloud account or app update settings do not exist on this client): 404 Not Found
