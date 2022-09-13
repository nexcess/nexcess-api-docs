# Portal: Enterprise Cloud

## enterprise-cloud:show-node
Shows details of an Enterprise Cloud Node.

**Endpoint**: GET /v1/enterprise-cloud/{cluster_id}/{node_id}

#### Access
service view permissions

#### Input
none

#### Request:
```
$ curl "$PORTAL_API/v1/enterprise-cloud/$CLUSTER_ID/$NODE_ID" \
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
