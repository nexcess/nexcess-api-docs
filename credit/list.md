# Portal: Credit

## credit:list
List Credits.

#### Access
credit view

#### Input
- integer `filter[id]` (optional): filter list by filter ID
- string `filter[type]` (optional): filter list by credit type
- string `filter[status]` (optional): filter list by credit status
- integer `match[id]` (optional): filter list by filter ID
- string `match[type]` (optional): filter list by credit type
- string `match[status]` (optional): filter list by credit status
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): sort list by id.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/credit" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 16 Dec 2021 13:06:08 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.4.3
Content-Range: items 1-1/1
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

[
  {
    "id": 30215,
    "identity": "Nexcess Staff - #30215",
    "metadata": {
      "scope": "credit",
      "uri": "/v1/credit/30215"
    },
    "status": "unapplied",
    "amount": "1000000.00",
    "applied_amount": "9716.80",
    "credit_date": 1543946191,
    "description": "Credit\n##LG_DEDUCTED## $10.00##LG_APPLIED_TO_INVOICE## #639382",
    "type": "credit"
  }
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
