# Portal: Enterprise Cloud

## enterprise-cloud:add
Orders a new Enterprise Cloud server cluster with at least one Node.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/enterprise-cloud

#### Access
service edit permissions
currently restricted to staff use only.

#### Input
- integer `cloud_id` (required): id of the cloud (location) to install the cloud server. @see cloud:list
- integer `package_id` (required): id of the virt-guest service package to order. @see package:list
- string|array `fiat` (required): the fiat (configuration) to use, as yaml or as a json object.
- bool `use_password` (optional): whether to set a root password for ssh login. A unique password will be automatically generated and provided via secure datashare (@see datashare:open) for each server. Using passwords for ssh is **strongly discouraged**; ssh keys should be used instead.
- integer[] `ssh_key_ids` (required if `use_password`=false): id of the ssh key(s) to install on the new cloud server. @see ssh-key:list
- integer[] `addon_ids` (optional): ids of package add-ons to order
- string `discount_code` (optional): discount code to apply to the order

#### Request:
```
$ curl -X POST "$PORTAL_API/v1/enterprise-cloud" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "cloud_id": 4,
    "package_id": 812,
    "fiat": {
      "environment": {
        "hardware": {
          "servers": [
            {
              "role": "lb",
              "network_type": "public",
              "public_ipv4_count": 1,
              "image": "centos-7-x86_64-latest",
              "flavor": "n5s-gp-1.tiny",
              "public_ip": true,
              "volume_size": 16
            },
            {
              "role": "fs",
              "quantity": 2,
              "network_type": "public",
              "public_ipv4_count": 1,
              "image": "centos-7-x86_64-latest",
              "flavor": "n5s-gp-1.tiny",
              "public_ip": true,
              "volume_size": 16
            }
          ]
        }
      }
    },
    "use_password": true
  }'
```

**Success Response** (request was accepted for processing): 202 Accepted
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

{
  "id":958,
  "identity":"enterprise-cloud:add (pending)",
  "metadata":{
    "scope":"api-task",
    "uri":"/v1/task/9702af0d-4893-4e05-a602-d2eaa5f4f33a"
  },
  "status":"pending",
  "action":"enterprise-cloud:add",
  "api_version":"0.5.0",
  "errors":{},
  "input":{},
  "request_date":1663069410,
  "resolved_date":null,
  "resource":null,
  "staff_user":null,
  "user":{
    "id":27767,
    "identity":"Annabel Whyman - user@nocworx.com",
    "metadata":{
      "scope":"user",
      "uri":"/v1/user/27767"
    }
  },
  "uuid":"9702af0d-4893-4e05-a602-d2eaa5f4f33a"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
