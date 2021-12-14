# Portal: Client

## client:history
Shows a history of events on the Client account.

#### Access
client view

#### Input
- integer `filter[id]` (optional): filter list by system ID.
- string `filter[action]` (optional): filter list by action.
- string `filter[scope]` (optional): filter list by scope.
- string `filter[user_id]` (optional): filter list by user id.
- integer `match[id]` (optional): match against system ID.
- string `match[action]` (optional): match against client action.
- string `match[scope]` (optional): match against scope.
- string `match[user_id]` (optional): match against user id.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `recent`|`id`|`event_date`|`action`|`scope`|`user_id`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl "$PORTAL_API_URL/v1/client/history" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 15 Nov 2021 12:51:27 GMT
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 751005,
    "identity": "api-task:store-edit - client:remove-tax-exempt (success) - 11/15/2021 06:28:55",
    "action": "store-edit",
    "event_date": 1636975735,
    "metadata": {
      "scope": "event",
      "uri": null
     },
    "resource": {
      "id": 479,
      "identity": "client:remove-tax-exempt (success)",
      "status": "success",
      "metadata": {
        "scope": "api-task",
        "uri": "/v1/task/3273d2de-e85f-491a-b6d9-0c60710446cf"
      }
    }
  },
  
  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
