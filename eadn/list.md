# Portal: Eadn

## eadn:list
Lists EADN Accounts.

#### Access
service view permission

#### Input
- integer `filter[id]` (optional): filter list by id
- integer `match[id]` (optional): filter list by id
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`type`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request:
```
$ curl -i "$PORTAL_API/v1/eadn" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 20 Jan 2022 10:57:01 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.4.3
Content-Range: items 1-5/5
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

[
  {
    "id": 137,
    "identity": "faithfulsortfeast.2100.lwdns.dev ##LG_CDN##",
    "metadata": {
      "scope": "eadn-account",
      "uri": "/v1/eadn/137"
    },
    "base_access_uri": "https://eadn-wc04-58593.nxedge.io",
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
    "enabled": true,
    "service": {
      "id": 58593,
      "identity": "##LG_EADN## (cdn): faithfulsortfeast.2100.lwdns.dev",
      "metadata": {
        "scope": "service",
        "uri": "/v1/service/eadn/58593"
      },
      "status": "enabled",
      "state": "stable",
      "type": "eadn"
    },
    "type": "cdn"
  },
...
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
