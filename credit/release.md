# Portal: Credit

## credit:redeem
Releases an available credit.

#### Access
credit view

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/credit/{id}/release" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 16 Dec 2021 13:24:10 GMT
Content-Type: application/json
Content-Length: 283
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 0,
  "identity": " - #0",
  "metadata": {
    "scope": "credit",
    "uri": "/v1/credit/0"
  },
  "status": "unapplied",
  "amount": "0.00",
  "applied_amount": "0.00",
  "client": null,
  "credit_date": 1639661050,
  "description": "",
  "invoice": null,
  "order": null,
  "payment": null,
  "reason": null,
  "service": null,
  "type": "credit"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (credit doesn't exist on your account): 404 Not Found
