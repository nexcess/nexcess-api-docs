# Portal: DNS Zones

## dns-zone:list
List DNS zones.

#### Access
dns zone view

#### Input
- integer `filter[id]` (optional): filter list by system ID
- integer `match` (optional): match against id value
- integer `range` (optional): find id values within .. range
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): sort list by id, domain.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/dns/zone" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 12 Jan 2022 13:20:52 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.4.3
Content-Range: items 1-11/11
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

[
  {
    "id": 18141,
    "identity": "m1-1944-test.com",
    "metadata": {
      "scope": "dns-zone",
      "uri": "/v1/dns/zone/18141"
    },
    "contact": "hostmaster@m1-1944-test.com",
    "domain": "m1-1944-test.com",
    "record_count": 16
  },
  {
    "id": 18142,
    "identity": "wordress.text.com",
    "metadata": {
      "scope": "dns-zone",
      "uri": "/v1/dns/zone/18142"
    },
    "contact": "hostmaster@wordress.text.com",
    "domain": "wordress.text.com",
    "record_count": 16
  },
  {
    "id": 18143,
    "identity": "test3.wordpress.com",
    "metadata": {
      "scope": "dns-zone",
      "uri": "/v1/dns/zone/18143"
    },
    "contact": "hostmaster@test3.wordpress.com",
    "domain": "test3.wordpress.com",
    "record_count": 16
  },
  {
    "id": 18144,
    "identity": "magento.com",
    "metadata": {
      "scope": "dns-zone",
      "uri": "/v1/dns/zone/18144"
    },
    "contact": "hostmaster@magento.com",
    "domain": "magento.com",
    "record_count": 16
  },
  {
    "id": 18145,
    "identity": "suspend.magentoi.com",
    "metadata": {
      "scope": "dns-zone",
      "uri": "/v1/dns/zone/18145"
    },
    "contact": "hostmaster@suspend.magentoi.com",
    "domain": "suspend.magentoi.com",
    "record_count": 16
  },
  {
    "id": 18146,
    "identity": "dev1safeharboraug12.lw-sre.app",
    "metadata": {
      "scope": "dns-zone",
      "uri": "/v1/dns/zone/18146"
    },
    "contact": "hostmaster@dev1safeharboraug12.lw-sre.app",
    "domain": "dev1safeharboraug12.lw-sre.app",
    "record_count": 16
  },
  {
    "id": 18147,
    "identity": "testcustomdomain.com",
    "metadata": {
      "scope": "dns-zone",
      "uri": "/v1/dns/zone/18147"
    },
    "contact": "hostmaster@testcustomdomain.com",
    "domain": "testcustomdomain.com",
    "record_count": 16
  },
  {
    "id": 18148,
    "identity": "magento2.next.com",
    "metadata": {
      "scope": "dns-zone",
      "uri": "/v1/dns/zone/18148"
    },
    "contact": "hostmaster@magento2.next.com",
    "domain": "magento2.next.com",
    "record_count": 16
  }
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
