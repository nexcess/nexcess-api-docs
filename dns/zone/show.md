# Portal: DNS Zones

## dns-zone:show
Show details of a dns zone.

#### Access
dns zone view permission

#### Input
none

#### Request:
```
$ curl -i "$PORTAL_API/v1/dns/zone/$ZONE_ID" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 12 Jan 2022 13:49:33 GMT
Content-Type: application/json
Content-Length: 414
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 18134,
  "identity": "test-again.com",
  "metadata": {
    "scope": "dns-zone",
    "uri": "/v1/dns/zone/18134"
  },
  "client": {
    "id": 38114,
    "identity": "Nexcess Staff",
    "metadata": {
      "scope": "client",
      "uri": null
    },
    "status": "active"
  },
  "contact": "hostmaster@test-again.com",
  "domain": "test-again.com",
  "expire": 1048576,
  "hosted": true,
  "minimum": 2560,
  "nameserver": "ns1.nexcess.net",
  "record_count": 20,
  "refresh": 7200,
  "retry": 2048,
  "serial": 1544116568
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
