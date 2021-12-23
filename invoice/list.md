# Portal: Invoice

## invoice:list
Lists a client's invoice.

#### Access
Invoice view permission

#### Input
- integer `filter[id]` (optional): filter list by id
- integer `filter[status]` (optional): filter list by status. @see invoice:status
- integer `filter[purchase_order_number]` (optional): filter list by purchase_order_number. @see invoice:purchase_order_number
- integer `match[id]` (optional): filter list by id
- integer `match[status]` (optional): filter list by status. @see invoice:list
- integer `match[purchase_order_number]` (optional): filter list by purchase_order_number. @see invoice:list
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`due`|`due_date`|`invoice_date`|`paid_date`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request:
```
$ curl -i "$PORTAL_API/v1/invoice" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 17 Jul 2019 01:50:28 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 1656
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.15
Content-Range: items 1-5/5
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

[
  {
    "id": 641792,
    "identity": "Annabel Whyman - user@nocworx.com",
    "metadata": {
      "scope": "invoice",
      "uri": "/v1/invoice/641792"
    },
    "status": "paid",
    "amount_due": "0.00",
    "due_date": 1636606799,
    "full_id": "641792-P",
    "has_payments": true,
    "invoice_date": 1636556874,
    "is_payable": null,
    "paid_date": 1636556876,
    "tax": "0.00",
    "total": "179.00"
   },

  . . .

]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
