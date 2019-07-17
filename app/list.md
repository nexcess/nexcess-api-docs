Portal: App
-----------

**since** 0.0.0

api-token:list
==============

Lists api tokens that belong to the logged-in user.

**Endpoint**:  GET /v1/app

**Access**: order view permission, or service edit permission

**Parameters**:
- string `filter[name]` (optional): filters results by app name.
- string `filter[version]` (optional): filters results by app version.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `type`|`id`|`name`|`version`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$PORTAL_API_URL/v1/app" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 17 Jul 2019 02:59:06 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 705
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.15
Content-Range: items 1-10/10
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

[
  {
    "id": 19,
    "identity": "BigCommerce for WordPress 1",
    "name": "BigCommerce for WordPress",
    "version": "1"
  },
  {
    "id": 23,
    "identity": "CraftCMS 3",
    "name": "CraftCMS",
    "version": "3"
  },
  {
    "id": 21,
    "identity": "Drupal 8",
    "name": "Drupal",
    "version": "8"
  },
  {
    "id": 24,
    "identity": "Expression Engine 5",
    "name": "Expression Engine",
    "version": "5"
  },
  {
    "id": 14,
    "identity": "Flexible ",
    "name": "Flexible",
    "version": ""
  },
  {
    "id": 12,
    "identity": "Magento 2",
    "name": "Magento",
    "version": "2"
  },
  {
    "id": 16,
    "identity": "OroCRM 1",
    "name": "OroCRM",
    "version": "1"
  },
  {
    "id": 22,
    "identity": "Sylius 1",
    "name": "Sylius",
    "version": "1"
  },
  {
    "id": 18,
    "identity": "WooCommerce 1",
    "name": "WooCommerce",
    "version": "1"
  },
  {
    "id": 20,
    "identity": "Wordpress 5",
    "name": "Wordpress",
    "version": "5"
  }
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
