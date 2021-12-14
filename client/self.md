# Portal: Client

## client:self
Shows details about the currently authenticated Client.

#### Access
logged-in users

#### Input
none

#### Request
```
$ curl "$PORTAL_API_URL/v1/client/self" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Thu, 11 Oct 2021 12:51:27 GMT
Content-Length: 44
NocWorx-Api-Version: 0.0.0

{
  "id": 38114,
  "identity": "Nexcess Staff",
  "status": "active",
  "affiliate": {
    "id": 38114,
    "identity": "Nexcess Staff",
    "is_affiliate": false,
    "metadata": {
      "scope": "client",
      "uri": null
    }
  },
  "billing": {
    "address": {
      "id": 12345,
      "identity": "first name last name",
      "address1": "21700 Melrose Ave",
      "address2": "21700 Melrose Ave",
      "city": "Southfield",
      "country": "US",
      "metadata": {
        "scope": "address",
        "uri": "/v1/address/12345"
      },
      "state": "MI",
      "type": "billing",
      "zip": "48075"
    },
    "amount_due": "0.00",
    "amount_overdue": "0.00",
    "credit_amount": "998380.90",
    "discount": null,
    "overdue_halt": false,
    "payment_type": "cc",
    "requires_creditcard": true,
    "tax_exempt": false,
  },
  "external_key": "",
  "external_key_prefix": null,
  "has_cancel_pending": false,
  "has_rdns_records": null,
  "metadata": {
    "scope": "client",
    "uri": null
  },
  "name": "My Company, Inc.",
  "owner": {
    "id": 61420,
    "identity": "Alice Bowman - alice@example.com",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  },
  "pin": "676867",
  "self_classification": "",
  "services": {
    "counts": {
      "eadn": {
        "production": 8
      },
      "cloud-account": {
        "development": 2,
        "production": 13
      }
    },
  },
  "start_date": 1543599098,
  "tax_exempt": {
    "number": ""
  }
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized
