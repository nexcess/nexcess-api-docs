# Portal: Tickets

## ticket:add
Creates a new customer support ticket.

Add requests are queued, meaning they will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
ticket edit permissions

#### Input
- string `department` (required): ticket department; one of support|billing|sales|migrations
- string `category` (optional): ticket category; one of application|autoscale|backups|cdn|container|dns|email|ip_blacklist|plugin_extension|provisioning_failure|resource_usage|security|site_down|ssl
- string `subject` (required): ticket subject line
- string `comment` (optional): initial ticket comment
- integer `service_id` (optional): system ID of client service the ticket is related to
- array `recipients` (optional): list of email addresses to be copied on the ticket

#### Request
```
$ curl -X POST "$PORTAL_API/v1/ticket" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{ "department": "support", "category": "dns", "subject": "It can't be DNS", "comment": "It was DNS." }'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Mon, 07 Feb 2022 11:42:11 GMT
Content-Type: application/json
Content-Length: 467
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 207,
  "identity": "ticket:add (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/69eb0630-c830-4e7c-b073-043825edb62d"
  },
  "status": "pending",
  "action": "ticket:add",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1644234130,
  "resolved_date": null,
  "resource": null,
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Nexcess Staff - nocworx-dev@nexcess.net",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  },
  "uuid": "69eb0630-c830-4e7c-b073-043825edb62d"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity

