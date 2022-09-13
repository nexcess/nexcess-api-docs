# Portal: Enterprise Cloud

## enterprise-cloud:remove-node
Removes a Node from an Enterprise Cloud Cluster.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: DELETE /v1/enterprise-cloud/{cluster_id}/{node_id}

#### Access
service edit permissions

#### Input
none

#### Request:
```
$ curl -X DELETE "$PORTAL_API/v1/enterprise-cloud/$CLUSTER_ID/$NODE_ID" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response**
```

```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
