# Portal: Enterprise Cloud

## enterprise-cloud:add-node
Adds a new Node to an Enterprise Cloud Cluster.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/enterprise-cloud/{cluster_id}/node

#### Access
service edit permissions

#### Input
none

#### Request:
```
$ curl -X POST "$PORTAL_API/v1/enterprise-cloud/$CLUSTER_ID/node" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json" \
  -H "Content-type: application/json" \
  -d '{
    "hostname": "another-server",
    "fiat": {
      "environment": {
        "hardware": {
          "servers": [
            {
              "role": "web",
              "network_type": "public",
              "public_ipv4_count": 1,
              "image": "centos-7-x86_64-latest",
              "flavor": "n5s-gp-1.tiny",
              "public_ip": true,
              "volume_size": 21
            }
          ]
        }
      }
    }
  }'
```

#### Responses
**Success Response**
```

```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
