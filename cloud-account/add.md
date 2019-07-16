Portal: Cloud Accounts
----------------------

**work in progress**

cloud-account:add
=================

**Endpoint**: POST /v1/cloud-account

**Access**: service edit permissions

**Parameters**:
- integer `app_id` (required): id of the app (wordpress, magento, etc.) to install on the cloud account. @see app:list
- integer `cloud_id` (required): id of the cloud (location) to install the cloud account. @see cloud:list
- string `domain` (required): domain name for the new cloud account
- bool `install_app` (optional): install the app (not all apps are installable)?
- integer `package_id` (required): id of the virt-guest-cloud service package to order. @see package:list

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/cloud-account" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{ "app_id": 123, "cloud_id": 45, "domain": "cloud-account.example.com", "install_app": true, "package_id": 678 }'
```

**Success Response**:
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Tue, 16 Jul 2019 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
X-Powered-By: PHP/7.2.15
Location: /v1/task/3b93d577-41ee-4077-913f-d36f91819bb9
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{ "id": 12, "identity": "cloud-account:add (pending)" }
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
