# Portal: EADN

## eadn:purge
Purges cache of eadn account.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
eadn view permissions

#### Input
none

#### Request:
```
$ curl -X POST "$PORTAL_API/v1/eadn/$EADN_ID/purge" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Thu, 20 Jan 2022 11:05:13 GMT
Content-Type: application/json
Content-Length: 600
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 206,
  "identity": "eadn:purge (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/339fe55f-6387-4c55-8423-8dc2ee21a464"
  },
  "status": "pending",
  "action": "eadn:purge",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1642676713,
  "resolved_date": null,
  "resource": {
    "id": 137,
    "identity": "faithfulsortfeast.2100.lwdns.dev ##LG_CDN##",
    "metadata": {
      "scope": "eadn-account",
      "uri": "/v1/eadn/137"
    },
    "type": "cdn"
  },
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Nexcess Staff - nocworx-dev@nexcess.net",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  },
  "uuid": "339fe55f-6387-4c55-8423-8dc2ee21a464"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
