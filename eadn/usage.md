# Portal: EADN

## eadn:usage
Shows EADN Account details.

#### Access
eadn view permission

#### Input
none

#### Request:
```
$ curl -i "$PORTAL_API/v1/eadn/$EADN_ID/usage" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 20 Jan 2022 11:04:16 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "cloud_account": {
    "id": 1418,
    "identity": "faithfulsortfeast.2100.lwdns.dev",
    "metadata": {
      "scope": "virt-guest-cloudaccount",
      "uri": "/v1/cloud-account/1418"
    },
    "status": "used",
    "state": "stable",
    "type": "account"
  },
  "eadn_account": {
    "id": 137,
    "identity": "faithfulsortfeast.2100.lwdns.dev ##LG_CDN##",
    "metadata": {
      "scope": "eadn-account",
      "uri": "/v1/eadn/137"
    },
    "type": "cdn",
    "included_bandwidth": 250,
    "monthly_fee": "0.00",
    "overage_fee": "0.10"
  },
  "usage": {
    "period": {
      "start": 1640235600,
      "end": 1642913999
    },
    "used": {
      "total": 0,
      "overage": 0,
      "cost": "0.00"
    }
  }
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
