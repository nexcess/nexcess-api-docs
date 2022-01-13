# Portal: DNS Zones

## dns-zone:add
Creates a new dns zone for the given domain  name.

#### Access
dns zone edit permissions

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Input
- string `domain` (required): domain name for the dns zone

#### Request
```
$ curl -X POST "$PORTAL_API/v1/dns/zone" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{ "domain": "test-domain.nexcess.com"}'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Wed, 12 Jan 2022 14:07:19 GMT
Content-Type: application/json
Content-Length: 471
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 198,
  "identity": "dns-zone:add (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/5f41b9cd-3939-48d4-865b-01c01efddd28"
  },
  "status": "pending",
  "action": "dns-zone:add",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1641996438,
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
  "uuid": "5f41b9cd-3939-48d4-865b-01c01efddd28"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
