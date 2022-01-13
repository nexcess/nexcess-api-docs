# Portal: DNS Reverse Records

## dns-reverse:add
Creates a new reverse DNS record.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
dns record edit permissions

#### Input
- string `ttl` (required): TTL (time to live) for the DNS Record.
- string `host` (required): Host name to add dns reverse.
- string `target` (required): Target for the DNS Record.

#### Request
```
$ curl -X POST "$PORTAL_API/v1/dns/reverse" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{"host" :  "203.0.113.1", "ttl" :  "1111", "target": "203.0.113.1"}'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Wed, 12 Jan 2022 14:49:46 GMT
Content-Type: application/json
Content-Length: 477
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 201,
  "identity": "dns-reverse:add (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/f46de2d4-77b6-4a1c-9181-ae15ed03aeb1"
  },
  "status": "pending",
  "action": "dns-reverse:add",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1641998986,
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
  "uuid": "f46de2d4-77b6-4a1c-9181-ae15ed03aeb1"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity

**Failure Response** (unwanted host ip): 422 Unprocessable Entity
