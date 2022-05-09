# Portal: DNS Records

## dns-zone:delete
Deletes a dns record.

#### Access
Dns record delete permissions

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Input
none

#### Request
```
$ curl -X DELETE "$PORTAL_API/v1/dns/record/$RECORD_ID" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Wed, 12 Jan 2022 14:19:41 GMT
Content-Type: application/json
Content-Length: 592
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 200,
  "identity": "dns-record:delete (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/64669836-cea8-4ac9-a59f-5c43daebf321"
  },
  "status": "pending",
  "action": "dns-record:delete",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1641997181,
  "resolved_date": null,
  "resource": {
    "id": 166730,
    "identity": "magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166730"
    },
    "type": "NS"
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
  "uuid": "64669836-cea8-4ac9-a59f-5c43daebf321"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found

**Failure Response** (cannot modify protected record): 422 Unprocessable Entity
