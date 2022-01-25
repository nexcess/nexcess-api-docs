# Portal: Event

## event:list
Lists Client events.

#### Access
event view permission

#### Input
- integer `filter[id]` (optional): filter list by id
- integer `filter[action]` (optional): filter list by action
- integer `filter[scope]` (optional): filter list by scope
- integer `filter[user_id]` (optional): filter list by user_id
- integer `match[id]` (optional): filter list by id
- integer `match[action]` (optional): filter list by action
- integer `match[scope]` (optional): filter list by scope
- integer `match[user_id]` (optional): filter list by user_id
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`recent`|`event_date`|`action`|`scope`|`user_id`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request:
```
$ curl -i "$PORTAL_API/v1/event" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 25 Jan 2022 10:32:47 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.4.3
Content-Range: items 1-25/4017
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

[
  {
    "id": 1352379,
    "identity": "api-task:store-edit - eadn:purge (success) - 01/20/2022 06:05:15",
    "metadata": {
      "scope": "event",
      "uri": null
    },
    "action": "store-edit",
    "event_date": 1642676715,
    "scope": "api-task"
  },
  {
    "id": 1352377,
    "identity": "api-task:store-add - eadn:purge (success) - 01/20/2022 06:05:13",
    "metadata": {
      "scope": "event",
      "uri": null
    },
    "action": "store-add",
    "event_date": 1642676713,
    "scope": "api-task"
  },
  {
    "id": 1352352,
    "identity": "api-task:store-edit - dns-record:edit (rejected) - 01/13/2022 02:39:04",
    "metadata": {
      "scope": "event",
      "uri": null
    },
    "action": "store-edit",
    "event_date": 1642059544,
    "scope": "api-task"
  }
 ...
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
