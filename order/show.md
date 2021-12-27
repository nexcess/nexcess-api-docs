# Portal: Order

## app:show
Shows Order details.

#### Access
order view

#### Request
```
$ curl "$PORTAL_API_URL/v1/order/$ORDER_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 27 Dec 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/order/1234
NocWorx-Api-Version: 0.0.0

{
  "id": 39873,
  "identity": "(39873) Howell Inc",
  "metadata": {
    "scope": "order",
    "uri": "/v1/order/39873"
  },
  "status": "allocated",
  "addons": [],
  "facility": null,
  "invoice": {
    "id": 639391,
    "identity": "Howell Inc - #639391",
    "metadata": {
      "scope": "invoice",
      "uri": "/v1/invoice/639391"
    },
    "status": "paid",
    "type": "pre-billed"
  },
  "order_date": 1544036415,
  "package": {
    "id": 716,
    "identity": "nc.small-test",
    "metadata": {
      "scope": "package",
      "uri": "/v1/package/716"
    },
    "status": "web-active",
    "type": "virt-guest-cloud"
  },
  "package_label": "nc.small-test",
  "service": null,
  "service_host": null,
  "service_id": 58239,
  "setup_fee": "0.00",
  "total": "10.00",
  "type": "virt-guest-cloud"
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
