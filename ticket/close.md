# Portal: Tickets

## ticket:close
Closes support ticket.

Add requests are queued, meaning they will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
ticket edit permissions

#### Input
none

#### Request
```
$ curl -X POST "$PORTAL_API/v1/ticket/$TICKET_ID/close" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
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
  "identity": "ticket:close (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/69eb0630-c830-4e7c-b073-043825edb62d"
  },
  "status": "pending",
  "action": "ticket:close",
 ...
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity

