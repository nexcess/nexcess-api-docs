# Portal: Invoice

## invoice:show
Show details of a invoice.

#### Access
invoice view permission

#### Input
none

#### Request:
```
$ curl -i "$PORTAL_API/v1/invoice/$INVOICE_ID" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Mon, 19 Aug 2019 02:23:34 GMT
Content-Type: application/json
Content-Length: 682
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.21
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 641792,
  "identity": "Annabel Whyman - user@nocworx.com",
  "metadata": {
    "scope": "invoice",
    "uri": "/v1/invoice/641792"
    },
  "status": "paid",
  "amount_due": "0.00",
  "bill_from": {
    "id": 71888,
    "identity": "first name last name",
    "metadata": {
      "scope": "address",
      "uri": "/v1/address/71888"
    },
    "address1": "21700 Melrose Ave",
    "address2": "",
    "city": "Southfield",
    "country": "US",
    "state": "MI",
    "type": "default",
    "zip": "48075"
  },
  "bill_to": {
    "id": 73411,
    "identity": "Annabel Whyman",
    "metadata": {
      "scope": "address",
      "uri": "/v1/address/73411"
    },
    "address1": "Jp Nagar16",
    "address2": "",
    "city": "Bangalore",
    "country": "CA",
    "state": "AB",
    "type": "default",
    "zip": "560076"
  },
  "client": {
    "id": 38116,
    "identity": "Annabel Whyman - user@nocworx.com",
    "metadata": {
      "scope": "client",
      "uri": null
    },
    "status": "active"
  },
  "due_date": 1636606799,
  "full_id": "641792-P",
  "has_payments": true,
  "invoice_date": 1636556874,
  "is_payable": false,
  "line_items": [
    {
      "description": "nc.medium",
      "price": "179.00",
      "quantity": 1,
      "total": "179.00",
      "type": "item"
   }
  ],
  "note": "",
  "order": {
    "id": 39926,
    "identity": "Annabel Whyman - user@nocworx.com",
    "metadata": {
      "scope": "order",
      "uri": "/v1/order/39926"
    },
    "status": "pending",
    "type": "virt-guest-cloud"
  },
  "paid_date": 1636556876,
  "purchase_order_number": "X1234567890",
  "tax": "0.00",
  "total": "179.00"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
