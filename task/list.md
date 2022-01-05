# Portal: Task

## task:list
Lists Tasks that have been requested by the current user/client.

#### Access
logged-in users

#### Input
- integer `filter[id]` (optional): filter list by system ID.
- integer `filter[uuid]` (optional): filter list by uuid.
- string `filter[action]` (optional): filter list by action.
- string `filter[status]` (optional): filter list by status.
- string `filter[user_id]` (optional): filter list by user id.
- integer `match[id]` (optional): match against system ID.
- integer `match[uuid]` (optional): match against uuid.
- string `match[action]` (optional): match against action.
- string `match[status]` (optional): match against status.
- string `match[user_id]` (optional): match against user id.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`latest`|`resolved_date`|`request_date`|`action`|`status`|`user_id`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/task" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Tue, 04 Jan 2022 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 491,
    "identity": "cloud-account:set-nickname (success)",
    "status": "success",
    "action": "cloud-account:set-nickname",
    "metadata": {
      "scope": "api-task",
      "uri": "/v1/task/279a64c9-e631-49f8-b5e6-5814aae05b78/"
    },
    "request_date": 1637834159,
    "resource": null,
    "staff_user": null,
    "user": {
      "id": 61420,
      "identity": "Alice Bowman - alice@example.com",
      "metadata": {
        "scope": "user",
        "uri": "/v1/user/61420/"
      }
    },
    "uuid": "279a64c9-e631-49f8-b5e6-5814aae05b78"
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
