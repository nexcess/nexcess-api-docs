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
  "id": 179,
  "identity": "SSL Certificate",
  "metadata": {
    "scope": "package",
    "uri": "/v1/package/179"
  },
  "addons": [],
  "auto_renew": true,
  "bandwidth": 0,
  "billing_type": "pre-billed",
  "configuration": {},
  "environment_type": "production",
  "is_wildcard": false,
  "label": "SSL Certificate",
  "name": "SSL Certificate",
  "orderable_terms": {
    "12": "##LG_ONE_YEAR##",
    "24": "##LG_TWO_YEARS##",
    "36": "##LG_THREE_YEARS##"
  },
  "term_fees": {
    "12": "29.95",
    "24": "49.96",
    "36": "69.96"
  },
  "trial_period": 0,
  "type": "ssl"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
