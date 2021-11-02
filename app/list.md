# Portal: App

## app:list
List Apps.

#### Access
app view

#### Input
- integer `filter[id]` (optional): filter list by system ID
- string `filter[name]` (optional): filter list by app name.
- string `filter[version]` (optional): filter list by app version.
- string `match[name]` (optional): match list by app name.
- string `match[version]` (optional): match list by app version.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `type`|`id`|`name`|`version`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/app" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Thu, 28 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 19,
    "identity": "BigCommerce for WordPress 1",
    "status": "active",
    "is_core_upgradable": true,
    "is_developerable": false,
    "is_installable": true,
    "is_plugin_upgradable": true,
    "is_wordpress_based": true,
    "metadata": {
      "scope": "app-app",
      "uri": "/v1/app/19"
    },
    "minimum_php_version": "5.6.20",
    "name": "BigCommerce for WordPress",
    "type": "bigcommerce",
    "version": "1"
  },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
