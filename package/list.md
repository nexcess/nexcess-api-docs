Portal: Package
---------------

**since** 0.0.0

package:list
============

Lists available packages (typically, of a particular type).

**Endpoint**:  GET /v1/package

**Alternate Endpoint**:  GET /v1/package/{type}

This alternate endpoint is sugar for `GET /v1/package?filter[type]={type}` and will serve identical responses.

For convenience, aliases are defined for several commonly used filters:

| since | **alias**                      | type             | environment_type |
|-------|--------------------------------|------------------|------------------|
| 0.0.0 | **cloud-account**              | virt-guest-cloud | production       |
| 0.5.0 | **cloud-account-free-trial**   | virt-guest-cloud | production-trial |
| 0.0.0 | **dev-cloud-account**          | virt-guest-cloud | development      |
| 0.0.0 | **staging-cloud-account**      | virt-guest-cloud | staging          |
| 0.5.0 | **staging-account-free-trial** | virt-guest-cloud | staging-trial    |
| 0.0.0 | **cloud-server**               | virt-guest       |                  |

**Access**: order view permission

**Parameters**:
- string `filter[type]` (optional): filters results by package type.
- string `filter[name]` (optional): filters results by package name.
- string `filter[monthly_fee]` (optional): filters results by package price.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`name`|`monthly_fee`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$PORTAL_API_URL/v1/package/cloud-account" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 18 Jul 2019 01:49:38 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 1150
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.15
Content-Range: items 1-11/11
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

[
  {
    "id": 707,
    "identity": "nc.xsmall",
    "name": "nc.xsmall",
    "monthly_fee": "29.00",
    "type": "virt-guest-cloud"
  },
  {
    "id": 708,
    "identity": "nc.small",
    "name": "nc.small",
    "monthly_fee": "99.00",
    "type": "virt-guest-cloud"
  },
  {
    "id": 709,
    "identity": "nc.medium",
    "name": "nc.medium",
    "monthly_fee": "179.00",
    "type": "virt-guest-cloud"
  },
  {
    "id": 710,
    "identity": "nc.large",
    "name": "nc.large",
    "monthly_fee": "299.00",
    "type": "virt-guest-cloud"
  },

  . . .

]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
