# Portal: CreditCard

## creditcard:show
Show Credit Card details.

#### Access
credit card view

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/creditcard/{id}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 28 Dec 2021 12:20:17 GMT
Content-Type: application/json
Content-Length: 350
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 39548,
  "identity": "Visa ************1111",
  "metadata": {
    "scope": "creditcard",
    "uri": "/v1/creditcard/39548"
  },
  "client": {
    "id": 38114,
    "identity": "Nexcess Staff",
    "metadata": {
      "scope": "client",
      "uri": null
    },
    "status": "active"
  },
  "expiration": 2219461199,
  "has_transactions": false,
  "is_primary": true,
  "name": "",
  "number": "************1111",
  "priority": 1,
  "type": "Visa"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found