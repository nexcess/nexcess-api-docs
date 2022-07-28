# Portal: Credit

## credit:show
Show Credit details.

#### Access
credit view

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/credit/{id}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 16 Dec 2021 13:01:18 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

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
  "client": {
    "id": 38114,
    "identity": "Nexcess Staff",
    "metadata": {
      "scope": "client",
      "uri": null
    },
    "status": "active"
  },
  "credit_date": 1543946191,
  "description": "Credit\n##LG_DEDUCTED## $10.00##LG_APPLIED_TO_INVOICE## #639382",
  "invoice": null,
  "order": null,
  "payment": null,
  "reason": {
    "id": 3,
    "identity": "##LG_OTHER##: ##LG_OTHER##",
    "metadata": {
      "scope": "credit-reason",
      "uri": null
    }
  },
  "service": null,
  "type": "credit"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
