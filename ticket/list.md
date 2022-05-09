# Portal: Tickets

## ticket:list
Lists a client's tickets.

#### Access
ticket view permission

#### Input
- integer `filter[id]` (optional): filter list by id
- integer `filter[subject]` (optional): filter list by subject
- integer `filter[status]` (optional): filter list by status
- integer `match[id]` (optional): filter list by id
- integer `match[subject]` (optional): filter list by subject
- integer `match[status]` (optional): filter list by status
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`subject`|`status`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request:
```
$ curl -i "$PORTAL_API/v1/ticket" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 17 Jul 2019 01:50:28 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 1656
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.15
Content-Range: items 1-5/5
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int
[
  {
    "company_id": 4,
    "id": 679942,
    "identity": "XJVV-1831",
    "client_id": 38114,
    "mask": "XJVV-1831",
    "subject": "TEST EMAIL 2",
    "recent_post": {
      "id": 4088412,
      "identity": "Nexcess Staff - 05\/13\/2020 04:26:34",
      "is_real": true,
      "meta": {
        "scope": "ticket-post"
      },
      "body": "test email 2",
      "name": "Nexcess Staff",
      "date": 1589358394,
      "reply_by": "client"
    },
    "last_reply_by": "client",
    "last_replier_name": "Nexcess Staff",
    "num_posts": 3,
    "num_posts_staff": 0,
    "update_date": 1589358395,
    "staff_update_date": 0,
    "client_update_date": 1589358394,
    "rating": 2,
    "category": {
      "id": 10,
      "identity": "Site Down",
      "is_real": true,
      "meta": {
        "scope": "ticket-category"
      }
    },
    "department": {
      "name": "Test",
      "color": "000000",
      "id": 98,
      "identity": "Test",
      "is_real": true
    },
    "priority": {
      "name": "Urgent",
      "color": "e60e0e",
      "id": 3,
      "identity": "Urgent",
      "is_real": true
    },
    "status": {
      "name": "Open",
      "color": "82bf3b",
      "id": 1,
      "identity": "Open",
      "is_real": true
    },
    "resolved_date": 0,
    "is_closed": false,
    "is_closeable": false
  }
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
