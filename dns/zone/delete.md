# Portal: DNS Zones

## dns-zone:delete
Deletes a dns zone.

#### Access
dns zone delete permissions

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Input
none

#### Request
```
$ curl -X DELETE "$PORTAL_API/v1/dns/zone/$ZONE_ID" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Wed, 12 Jan 2022 14:04:25 GMT
Content-Type: application/json
Content-Length: 572
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 197,
  "identity": "dns-zone:delete (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/647fbe24-a9d5-4c29-bd57-dee50f6b033c"
  },
  "status": "pending",
  "action": "dns-zone:delete",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1641996265,
  "resolved_date": null,
  "resource": {
    "id": 18134,
    "identity": "test-again.com",
    "metadata": {
      "scope": "dns-zone",
      "uri": "/v1/dns/zone/18134"
    }
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
  "uuid": "647fbe24-a9d5-4c29-bd57-dee50f6b033c"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found

**Failure Response** (cannot delete reserved zone): 422 Unprocessable Entity

**Failure Response** (cannot delete RDNS zone): 422 Unprocessable Entity
