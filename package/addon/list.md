Portal: Package Addon
---------------------

**since** 0.0.0

package-addon:list
==================

Lists package addons (typically, belonging to a particular package).

**Endpoint**:  GET /v1/package/addon

**Alternate Endpoint**:  GET /v1/package/{id}/addon

This alternate endpoint is sugar for `GET /v1/package/addon?filter[package_id]={id}` and will serve identical responses.

**Access**: order view permission

**Parameters**:
- string `filter[package_id]` (optional): filters results by package
- integer `page` (optional): 1-based result set count for paginated results
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list
- string `sortBy` (optional): field to sort the list by; (sortable fields TBD)
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`

**Request**:
```
curl -i "$PORTAL_API_URL/v1/package/$PACKAGE_ID/addon" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
