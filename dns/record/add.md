# Portal: DNS Records

## dns-record:add
Creates a new Dns Record for the given zone id.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
dns record edit permissions

#### Input
- integer `zone_id` (required): System id of the DNS Zone for this Record.
- string `type` (required): Type of DNS Record to add.
- string `ttl` (required): TTL (time to live) for the DNS Record.
- string `host` (optional): Host to add dns record.
- string `target` (optional): Target for the DNS Record.

#### Request
```
$ curl -X POST "$PORTAL_API/v1/dns/record" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{"zone_id": "18143", "type" :  "AAAA", "host" :  "www", "ttl" :  "1111"}'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Wed, 12 Jan 2022 14:12:44 GMT
Content-Type: application/json
Content-Length: 475
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 199,
  "identity": "dns-record:add (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/452c3de1-c418-4dcd-b2b5-695aebddf459"
  },
  "status": "pending",
  "action": "dns-record:add",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1641996764,
  "resolved_date": null,
  "resource": null,
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Nexcess Staff - nocworx-dev@nexcess.net",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  },
  "uuid": "452c3de1-c418-4dcd-b2b5-695aebddf459"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity

**Failure Response** (cannot modify protected record): 422 Unprocessable Entity

**Failure Response** (duplicate entry): 422 Unprocessable Entity
