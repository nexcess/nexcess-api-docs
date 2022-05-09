# Portal: Os Template

## os-template:list
Lists Operating System install templates available for cloud servers.

#### Access
os view

#### Input
- integer `filter[id]` (optional): filter list by system ID.
- integer `filter[name]` (optional): filter list by template name.
- integer `filter[os]` (optional): filter list by os name.
- string `match[id]` (optional): match against system ID.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`name`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.status

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/os-template" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Thu, 30 Dec 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 3,
    "identity": "CentOS 6 x64",
    "status": "web-active",
    "metadata": {
      "scope": "operating-system-install-template",
      "uri": "/v1/os-template/3/"
    }
  },
  {
    "id": 4,
    "identity": "CentOS 7 x64",
    "status": "web-active",
    "metadata": {
      "scope": "operating-system-install-template",
      "uri": "/v1/os-template/4/"
    }
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
