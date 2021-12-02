# Portal: Cloud Account

## cloud-account:show-eadn-account-details
Shows EADN Account details.

#### Access
eadn account view

#### Input
- string `cloud_account_id` (required): cloud account id; The system id of the cloud account that the eadn account belongs to.

#### Request
```
$ curl "$PORTAL_API_URL/v1/cloud-account/{cloud_account_id}/eadn" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 22 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/cloud-account/12345/eadn
NocWorx-Api-Version: 0.0.0

{
  "id": 196976,
  "identity": "4bd2e3b804.100.lwdns.dev ##LG_CDN##",
  "metadata": {
    "scope": "eadn-account",
    "uri": "/v1/eadn/196976"
  },
  "base_access_uri": "https://eadn-wc03-197052.nxedge.io",
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
  "enabled": true,
  "service": {
    "id": 197052,
    "identity": "##LG_EADN## (cdn): 4bd2e3b804.100.lwdns.dev",
    "metadata": {
      "scope": "service",
      "uri": "/v1/service/eadn/197052"
    },
    "status": "enabled",
    "state": "stable",
    "type": "eadn"
  },
  "type": "cdn"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
