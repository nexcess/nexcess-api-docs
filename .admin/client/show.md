Admin: Clients
--------------

**since** 0.2.0

client:show
===========

Shows Client account details.

**Endpoint**:  GET /v1/client/{id}

**Access**: client view permission

**Request**:
```
curl -i "$ADMIN_API_URL/v1/client/$COMPANY_ID-$EXTERNAL_KEY" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 26 Sep 2019 12:40:12 GMT
Content-Type: application/json
Content-Length: 2930
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.21
NocWorx-Api-Version: 0.1.0
Served-By: nwdev-web01-int

{
  "id": 24512,
  "identity": "Bosco-Bradtke",
  "status": "active",
  "affiliate_info": {
    "is_affiliate": true,
    "status": "active",
    "address": {
      "id": 73389,
      "identity": "Net Nexcess",
      "uri": null
    },
    "affiliate_payout_type": "credit",
    "affiliate_suspended": 0,
    "level": {
      "id": 3,
      "identity": "Recurring Affiliate 10%",
      "uri": null
    }
  },
  "billing_address": null,
  "company": {
    "id": 4,
    "identity": "Nexcess",
    "uri": null
  },
  "credit_amount": "99,628.76",
  "external_key": "",
  "has_agent": false,
  "has_cancel_pending": false,
  "has_rdns_records": null,
  "has_rdnsable_ips": true,
  "mrc": "559.08",
  "name": "Bosco-Bradtke",
  "open_tickets": [
    {
      "id": 679937,
      "identity": "BEYP-3645",
      "uri": null
    },

    . . .

  ],
  "owner": {
    "id": 27767,
    "identity": "Annabel Whyman - user@nocworx.com",
    "uri": null
  },
  "payment_type": "cc",
  "pin": "418112",
  "prominence": "normal",
  "referred_date": 0,
  "referrer": null,
  "requires_creditcard": true,
  "services": [
    {
      "id": 58275,
      "identity": "us-midwest-1 - cloud-server-example - 207.32.181.23",
      "uri": null
    },

    . . .

  ],
  "start_date": 1375738296,
  "tags": [],
  "users": [
    {
      "id": 61415,
      "identity": "iherzog@example.org",
      "uri": null
    },
    {
      "id": 27767,
      "identity": "user@nocworx.com",
      "uri": null
    }
  ]
}

```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
