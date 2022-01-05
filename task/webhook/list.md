# Portal: Webhook

## webhook:list
Lists registered webhooks.

#### Access
webhook users

#### Input
- integer `filter[id]` (optional): filter list by system ID.
- integer `filter[name]` (optional): filter list by name.
- string `filter[resource]` (optional): filter list by the resource it listens to.
- string `filter[action]` (optional): filter list by the action it listens to.
- string `filter[url]` (optional): filter list by url.
- integer `match[id]` (optional): match against system ID.
- integer `match[name]` (optional): match against name.
- string `match[resource]` (optional): match against resource it listens to.
- string `match[action]` (optional): match against action it listens to.
- string `match[url]` (optional): match against url.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`name`|`listen_to`|`url`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/task/webhook" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 05 Jan 2022 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 1,
    "identity": "#1 My First Webhook",
    "client": {
      "id": 38114,
      "identity": "Alice Bowman",
      "status": "active",
      "metadata": {
        "scope": "client",
        "uri": null
      }
    },
    "listen_to": {
      "resource": "webhook",
      "action": "laptop"
    },
    "metadata": {
      "scope": "api-webhook",
      "uri": "/v1/task/webhook/1/"
    },
    "name": "My First Webhook",
    "url": "https://example.com/webhook"
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
