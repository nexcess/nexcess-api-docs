Admin: Service
--------------

service:show
============

Shows details of a client service.

**Endpoint**:  GET /v1/service/{id}

**Alternate Endpoint**:  GET /v1/service/{type}/{id}

This alternate endpoint adds type-specific information to the response payload. When no type is specified, a generic service payload is returned.

For convenience, the following type aliases are defined:

| **alias**         | type             |
|-------------------|------------------|
| **cloud-account** | virt-guest-cloud |
| **cloud-server**  | virt-guest       |

**Access**: service view permission

**Parameters**:
none.

**Request**:
```
curl -i "$ADMIN_API_URL/v1/service/$SERVICE_ID" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Fri, 24 Jan 2020 04:23:45 GMT
Content-Type: application/json
Content-Length: 888
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.26
NocWorx-Api-Version: 0.4.0
Served-By: nwdev-web01-int

{
  "id": 12345,
  "identity": "us-midwest-1 - example-service.com - 203.0.113.1",
  "status": "enabled",
  "addons": [],
  "billing_info": {
    "type": "monthly",
    "amount": "20.00",
    "is_overdue": false,
    "last_bill_date": 0,
    "next_bill_date": 1579755600,
    "bill_day": "23",
    "auto_renew": "yes"
  },
  "cancellation_info": {
    "can_cancel": true
  },
  "client": {
    "id": 23456,
    "identity": "Sample Inc.",
    "metadata": {
      "scope": "client",
      "uri": null
    }
  },
  "contract": null,
  "discount": null,
  "external_key": "",
  "metadata": {
    "scope": "service",
    "uri": "/v1/service/cloud-server/12345/"
  },
  "nickname": "",
  "order": {
    "id": 67890,
    "identity": "(67890) Sample Inc.",
    "metadata": {
      "scope": "order",
      "uri": "/v1/order/67890/"
    }
  },
  "package": {
    "id": 456,
    "identity": "LW MH Cloud Cluster",
    "metadata": {
      "scope": "package",
      "uri": "/v1/package/456/"
    }
  },
  "parent": null,
  "paypal_subscription_info": {
    "can_subscribe": false
  },
  "start_date": 1579785424,
  "state": "stable",
  "type": "virt-guest"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (does not exist): 404 Not Found
