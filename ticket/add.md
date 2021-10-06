Portal: Tickets
---------------

ticket:add
==========

Creates a new customer support ticket.

Add requests are queued, meaning they will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/ticket

**Access**: ticket edit permissions

**Parameters**:
- string `department` (required): ticket department; one of support|billing|sales|migrations
- string `category` (optional): ticket category; one of application|autoscale|backups|cdn|container|dns|email|ip_blacklist|plugin_extension|provisioning_failure|resource_usage|security|site_down|ssl
- string `subject` (required): ticket subject line
- string `comment` (optional): initial ticket comment
- integer `service_id` (optional): system ID of client service the ticket is related to
- array `recipients` (optional): list of email addresses to be copied on the ticket

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/ticket" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{ "department": "support", "category": "dns", "subject": "It can't be DNS", "comment": "It was DNS." }'
```

**Success Response**: 202 Accepted
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

{ "id": 1234, "identity": "ticket:add (pending)" }
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
