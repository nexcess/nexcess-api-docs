# Portal: DNS Records

## dns-record:show
Shows Dns Record details.

#### Access
dns record view permission

#### Input
none

#### Request:
```
$ curl -i "$PORTAL_API/v1/dns/record/$RECORD_ID" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 12 Jan 2022 14:30:31 GMT
Content-Type: application/json
Content-Length: 189
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 166731,
  "identity": "magento.com",
  "metadata": {
    "scope": "dns-record",
    "uri": "/v1/dns/reverse/166731"
  },
  "host": "",
  "target": "ns2.nexcess.net",
  "ttl": 86400,
  "type": "NS",
  "update_date": 1595850600
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
