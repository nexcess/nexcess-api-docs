# Portal: Client

## client:hud
Lists "Heads-Up Display" Notifications for the currently authenticated User.

#### Access
logged-in users

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/client/hud" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 15 Nov 2021 12:51:27 GMT
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "cloudaccount_id": 1123,
    "state": "failure",
    "nickname": "",
    "client_domain": "",
    "domain": "afd47862cd.1700.lwdns.dev",
    "plan_id": 58432,
    "plan_nickname": "Magento nc.small-test Plan 4",
    "package_label": "nc.small-test",
    "package_is_plan": false,
    "app_name": "Magento",
    "app_is_wordpress_based": false,
    "environment_access_username": "admin",
    "environment_access_url": "https://afd47862cd.1700.lwdns.dev/ae55c48638_admin",
    "notification": "cloud-account:status"
  },
  
  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
