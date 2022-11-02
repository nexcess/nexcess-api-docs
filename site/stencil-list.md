# Portal: Site

## site:stencil-list
Lists Stencils.

#### Access
service view

#### Input
- integer `account_id` (optional): System ID of the Site to view
- string `filter[name]` (optional): filter list by Site name.
- string `filter[service_id]` (optional): filter list by service id.
- string `filter[state]` (optional): filter list by Site state.
- integer `filter[stencil_date]` (optional): filter list by stencil date.
- integer `match[id]` (optional): match against system ID.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `name`|`state`|`stencil_date`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl "$PORTAL_API_URL/v1/site/{account_id}/stencil" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 22 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/site/12345/stencil
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 9,
    "identity": "wednesday",
    "metadata": {
      "scope": "virt-guest-cloudaccount-stencil",
      "uri": "/v1/site/stencil/9"
    },
    "app_type": "wordpress",
    "app_version": "5.8.1",
    "site": {
      "id": 1206,
      "identity": "a84cb86096.100.lwdns.dev",
      "metadata": {
        "scope": "virt-guest-cloudaccount",
        "uri": "/v1/site/1206"
      },
      "status": "used",
      "state": "stable",
      "type": "account"
    },
    "name": "wednesday",
    "screenshot_url": "https://objects.liquidweb.services/mirador-dev/site/24512/virt-guest-cloudaccount-stencil-9/5089e29e-dda8-46b1-951a-b9911528efbc.png",
    "screenshot_uuid": "5089e29e-dda8-46b1-951a-b9911528efbc",
    "state": "stable",
    "stencil_date": 1638367171,
    "url": "https://objects.liquidweb.services/SZGPEA/stencils/stencil-1206-9.tgz"
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
