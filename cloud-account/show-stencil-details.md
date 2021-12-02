# Portal: Cloud Account

## cloud-account:show-stencil-details
Shows Stencil details.

#### Access
stencil view

#### Input
- integer `account_id` (optional): System ID of the cloud account that the stencil belongs to.

#### Request
```
$ curl "$PORTAL_API_URL/v1/cloud-account/{account_id}/stencil/{id}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json" 
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Thu, 25 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/cloud-account/1004/stencil/12345
NocWorx-Api-Version: 0.0.0

{
  "id": 9,
  "identity": "wednesday",
  "metadata": {
    "scope": "virt-guest-cloudaccount-stencil",
    "uri": "/v1/cloud-account/stencil/9"
  },
  "app_type": "wordpress",
  "app_version": "5.8.1",
  "cloud_account": {
    "id": 1206,
    "identity": "a84cb86096.100.lwdns.dev",
    "metadata": {
      "scope": "virt-guest-cloudaccount",
      "uri": "/v1/cloud-account/1206"
    },
    "status": "used",
    "state": "stable",
    "type": "account"
  },
  "name": "wednesday",
  "screenshot_url": "https://objects.liquidweb.services/mirador-dev/site/24512/virt-guest-cloudaccount-stencil-9/5089e29e-dda8-46b1-951a-b9911528efbc.png",
  "screenshot_uuid": "5089e29e-dda8-46b1-951a-b9911528efbc",
  "state": "stable",
  "stencil_date": 1638367171,
  "url": "https://objects.liquidweb.services/SZGPEA/stencils/stencil-1206-9.tgz"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
