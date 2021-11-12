# Portal: Affiliate

## affiliate:show
Show Affiliate Link with list of Stats.

#### Access
affiliate referral link view

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/affiliate-link/{id}/stats" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (request was accepted for processing): 200 OK
```
HTTP/1.1 200 OK
Date: Fri, 05 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "name": "Magento Hosting",
    "target_url": "http://www.nexcess.net/magento-hosting"
    "status": "active",
    "metadata": {
      "creation_date": 1431725299,
      "ip": "192.240.191.2",
      "referrer": "http://businesssolutionsinthecloud.com/magento-hosting-uk",
      "query_string": "item=MjAyNzV8MQ",
      "order": 123,
      "commission": 0.5
    }
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
