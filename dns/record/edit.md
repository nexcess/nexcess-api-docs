# Portal: DNS Records

## dns-record:edit
Edits a stored Dns Record.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
dns record edit permissions

#### Input
- integer `id` (required): System id of the DNS record.
- string `type` (optional): Type of DNS Record to add.
- string `ttl` (optional): TTL (time to live) for the DNS Record.
- string `host` (optional): Host to add dns record.
- string `target` (optional): Target for the DNS Record.

#### Request
```
$ curl -X POST "$PORTAL_API/v1/dns/record/$RECORD_ID" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{"type" :  "A"}'
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
  "identity": "dns-record:edit (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/7389da2e-91f9-4e30-9400-8764176431e9"
  },
  "status": "pending",
  "action": "dns-record:edit",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1642059542,
  "resolved_date": null,
  "resource": {
    "id": 166813,
    "identity": "magento2.next.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166813"
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
  "uuid": "7389da2e-91f9-4e30-9400-8764176431e9"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
