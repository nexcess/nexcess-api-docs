# Portal: Cloud Account

## cloud-account:show-eadn-account-details
Shows EADN Account Usage details.

#### Access
eadn account usage view

#### Input
- string `cloud_account_id` (required): cloud account id; The system id of the cloud account that the eadn account belongs to.

#### Request
```
$ curl "$PORTAL_API_URL/v1/cloud-account/{cloud_account_id}/eadn/usage" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 23 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/cloud-account/12345/eadn/usage
NocWorx-Api-Version: 0.0.0

{
  "cloud_account": {
    "id": 1204,
    "identity": "4bd2e3b804.100.lwdns.dev",
    "metadata": {
      "scope": "virt-guest-cloudaccount",
      "uri": "/v1/cloud-account/1204"
    },
    "status": "used",
    "state": "stable",
    "type": "account"
  },
  "eadn_account": {
    "id": 196976,
    "identity": "4bd2e3b804.100.lwdns.dev ##LG_CDN##",
    "metadata": {
      "scope": "eadn-account",
      "uri": "/v1/eadn/196976"
    },
    "type": "cdn",
    "included_bandwidth": 250,
    "monthly_fee": "0.00",
    "overage_fee": "0.10"
  },
  "usage": {
    "period": {
      "start": 1637643600,
      "end": 1640235599
    },
    "used": {
      "total": 0,
      "overage": 0,
      "cost": "0.00"
    }
  }
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
