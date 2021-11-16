# Portal: Cloud Servers

## cloud-server:add
Creates a new cloud server and orders an associated service.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
service edit permissions

#### Input
- integer `cloud_id` (required): id of the cloud (location) to install the cloud server. @see cloud:list
- string `hostname` (required): host name for the new cloud server
- integer `package_id` (required): id of the virt-guest service package to order. @see package:list
- integer `os_id` (required): id of the operating system install template to use. @see os:list
- bool `use_password` (optional): whether to set a root password for ssh login. Note, the password will be automatically generated and provided via secure datashare (@see datashare:open). Using passwords for ssh is **strongly discouraged**; ssh keys should be used instead.
- integer[] `ssh_key_ids` (required if `use_password`=false): id of the ssh key(s) to install on the new cloud server. @see ssh-key:list
- integer[] `addon_ids` (optional): ids of service add-on packages to order
- string `discount_code` (optional): discount code to apply to the order

#### Request
```
$ curl -X POST "$PORTAL_API/v1/cloud-server" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{ "cloud_id": 1, "hostname": "cloud-server-example", "package_id": 677, "os_id": 4, "ssh_key_ids": [138, 139] }'
```

#### Responses
**Success Response** (request was created for processing): 202 Accepted
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

{ "id": 12, "identity": "cloud-server:add (pending)" }
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
