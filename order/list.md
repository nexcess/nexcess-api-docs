# Portal: Order

## order:list
List Orders.

#### Access
order view

#### Input
- integer `filter[id]` (optional): filter list by system ID.
- string `filter[type]` (optional): filter list by order type.
- string `filter[status]` (optional): filter list by order status.
- string `match[id]` (optional): match against system ID.
- string `match[type]` (optional): match against order type.
- string `match[status]` (optional): match against order status.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`order_date`|`order_total`|`status`|`type`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/order" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 27 Dec 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 39859,
    "identity": "(39859) Howell Inc",
    "metadata": {
      "scope": "order",
      "uri": "/v1/order/39859"
    },
    "status": "allocated",
    "invoice": {
      "id": 639381,
      "identity": "Howell Inc - #639381",
      "metadata": {
          "scope": "invoice",
          "uri": "/v1/invoice/639381"
      },
      "status": "paid",
      "type": "pre-billed"
    },
    "order_date": 1543599182,
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
    "service": {
      "id": 58412,
      "identity": "b3c05af14a.1700.lwdns.dev - nc.small-test",
      "metadata": {
        "scope": "service",
        "uri": "/v1/service/cloud-account/58412"
      },
      "status": "enabled",
      "state": "failure",
      "type": "virt-guest-cloud"
    },
    "service_id": 58412,
    "total": "10.00",
    "type": "virt-guest-cloud"
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
