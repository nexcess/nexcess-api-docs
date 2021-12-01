# Portal: Cloud Account

## cloud-account:stencil-list
Lists Stencils.

#### Access
stencil view

#### Input
- integer `account_id` (optional): System ID of the cloud account to view
- string `filter[name]` (optional): filter list by cloud account name.
- string `filter[service_id]` (optional): filter list by service id.
- string `filter[state]` (optional): filter list by cloud account state.
- integer `filter[stencil_date]` (optional): filter list by stencil date.
- integer `match[id]` (optional): match against system ID.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `name`|`state`|`stencil_date`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl "$PORTAL_API_URL/v1/cloud-account/{account_id}/stencil" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 22 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/cloud-account/12345/stencil
NocWorx-Api-Version: 0.0.0

[]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
