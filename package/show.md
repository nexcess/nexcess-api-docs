Portal: Package
---------------

**since** 0.0.0

package:show
============

Shows package details.

**Endpoint**:  GET /v1/package/{id}

**Access**: order view permission

**Parameters**: none

**Request**:
```
curl -i "$PORTAL_API_URL/v1/package/$PACKAGE_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 18 Jul 2019 02:18:30 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 284
X-Powered-By: PHP/7.2.15
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 707,
  "identity": "nc.xsmall",
  "name": "nc.xsmall",
  "monthly_fee": "29.00",
  "type": "virt-guest-cloud",
  "configuration": {
    "packagetemplate": "nc_xsmall",
    "environment": {
      "hardware": {
        "servers": [
          {
            "role": "cloudhost",
            "image": "centos-7-x86_64-latest",
            "flavor": "n5s-sc-1.dev",
            "public_ip": true
          }
        ]
      }
    }
  }
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
