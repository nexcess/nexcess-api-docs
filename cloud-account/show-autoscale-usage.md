# Portal: Cloud Account

## cloud-account:show-autoscale-usage-details
Shows autoscale usage data.

#### Access
logged-in users

#### Input
- integer `id` (optional): System ID of the eadn account to edit
- string `cloud_account_id` (optional): cloud account id; The system id of the cloud account that the eadn account belongs to.

#### Request
```
$ curl "$PORTAL_API_URL/v1/cloud-account/{id}/autoscale-usage" \
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
  "billable_cost": 0,
  "billable_used": 0,
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
  "minutes_grace": {
    "start": 1440,
    "end": 1440
  },
  "period": {
    "start": 1637643600,
    "end": 1640235599
  },
  "used": 0
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
