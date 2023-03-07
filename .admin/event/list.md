Admin: Event
------------

event:list
==========

Lists events.

**Endpoint**:  GET /v1/event

**Alternate Endpoint**:  GET /v1/client/{client_id}/event

This alternate endpoint is sugar for `GET /v1/event?filter[client_id]={client_id}`.

**Access**: event view permission

**Parameters**:
- int `filter[client_id]` (optional): filters results by client.
- string `filter[action]` (optional): filters results by the event action.
- string `filter[scope]` (optional): filters results by resource scope.
- string `filter[user_id]` (optional): filters results by User (the admin user, if any) id.
- string `filter[client_user_id]` (optional): filters results by ClientUser (if any) id.
- string `filter[ip]` (optional): filters results by IP the causal request came from (if any).
- string `filter[priority]` (optional): filters results by priority; one of `info`|`warning`|`error`|`critical`.
- string `match[action]` (optional): matches results by the event action. 
- string `range[event_date]` (optional): range results by start..stop date (unixtime) or by `recent` (last 30 days).
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`parent_id`|`start_date`|`status`|`state`|`type`|`nickname`|`external_key`|`last_bill_date`|`next_bill_date`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$ADMIN_API_URL/v1/event" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 16 Jan 2020 02:59:56 GMT
Content-Type: application/json
Content-Length: 11699
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.21
Content-Range: items 1-22/22
NocWorx-Api-Version: 0.3.0
Served-By: nwdev-web01-int

[
  {
    "id": 12345,
    "identity": "service:store-add - n5s.large - 0.0.0.0/24 - 08/07/2017 10:55:14",
    "metadata": { "scope": "event", "uri": "/v1/event/12345" },
    "scope": "service",
    "action": "store-add",
    "user": {
      "id": 23456,
      "identity": "staff@nexcess.net",
      "metadata": { "scope": "user", "uri": null }
    },
    "client_user": {
      "id": 34567,
      "identity": "user@example.com",
      "metadata": { "scope": "client-user", "uri": null }
    },
    "client": {
      "id": 45678,
      "identity": "Example, LLC",
      "metadata": { "scope": "client-user", "uri": "/v1/client/45678" }
    },
    "ip": "203.0.113.1"
  },

  . . .

]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
