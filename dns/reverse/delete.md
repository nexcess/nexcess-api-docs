# Portal: DNS Reverse Records

## dns-reverse:delete
Deletes a Reverse DNS Record.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
Dns reverse record delete permissions.

#### Input
none

#### Request
```
$ curl -X DELETE "$PORTAL_API/v1/dns/reverse/$RECORD_ID" \
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
  "identity": "dns-reverse:delete (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/64669836-cea8-4ac9-a59f-5c43daebf321"
  },
...
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
