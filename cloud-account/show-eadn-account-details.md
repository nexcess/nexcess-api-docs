# Portal: Cloud Account

## cloud-account:show-eadn-account-details
Shows EADN Account details.

#### Access
eadn account view

#### Input
- integer `id` (optional): System ID of the eadn account to edit
- string `cloud_account_id` (optional): cloud account id; The system id of the cloud account that the eadn account belongs to.

#### Request
```
$ curl "$PORTAL_API_URL/v1/cloud-account/{cloud_account_id}/eadn" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json" \
  -d '{
    "id":1234
  }'
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 22 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/cloud-account/12345/eadn
NocWorx-Api-Version: 0.0.0

{}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
