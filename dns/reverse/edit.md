# Portal: DNS Reverse Records

## dns-reverse:edit
Edits a stored Dns Reverse Record.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
dns reverse record edit permissions

#### Input
- string `ttl` (optional): TTL (time to live) for the DNS Record.
- string `host` (optional): Host name to add dns reverse.
- string `target` (optional): Target for the DNS Record.

#### Request
```
$ curl -X POST "$PORTAL_API/v1/dns/reverse/$RECORD_ID" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{"ttl" :  "1111"}'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Thu, 13 Jan 2022 07:39:03 GMT
Content-Type: application/json
Content-Length: 594
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 202,
  "identity": "dns-reverse:edit (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/7389da2e-91f9-4e30-9400-8764176431e9"
  },
  "status": "pending",
  "action": "dns-reverse:edit",
...
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
