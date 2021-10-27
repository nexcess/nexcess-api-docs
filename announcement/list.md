# Portal: Announcement

## address:list
Lists Announcements.

#### Access
announcement view

#### Input
- integer `filter[id]` (optional): filter list by system ID
- integer `match` (optional): match against id value
- integer `range` (optional): find id values within .. range
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`post_date`|`title`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/announcement" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 19 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/announcement
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 773,
    "identity": "#773 [February 17, 2016] glibc update",
    "status": "active",
    "body": "Date: February 17, 2016\nStart time: 2 p.m. eastern standard time (EST)\nEstimated end-time: 3 p.m. eastern standard time (EST)\nLocation: All locations\nServices affected: php-fpm\nDevices affected: All Centos 6 & 7 servers\nReason: Critical Security Update\nClients affected: Clients on managed servers\n\nDescription: glibc will be updated to apply a critical security update to fix CVE-2015-7547.\n\nRegression plan: While this update has been tested thoroughly, the update will be rolled back should there be any issues.",
    "metadata": {
      "scope": "announcement",
      "uri": "/v1/announcement/773"
    },
    "post_date": 1455685200,
    "title": "[February 17, 2016] glibc update"
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
