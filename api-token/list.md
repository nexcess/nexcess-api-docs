Portal: Api Tokens
------------------

**since** 0.0.0

api-token:list
==============

Lists api tokens that belong to the logged-in user.

**Endpoint**:  GET /v1/api-token

**Access**: logged-in users

**Parameters**:
- `filter[name]`: Optional: filters results by token name.
- `filter[id]`: Optional: filters results by token id.
- `page`: Optional: 1-based result set count for paginated results.
- `pageSize`: Optional: maximum number of results to include per "page" of a paginated list.
- `sortBy`: Optional: field to sort the list by; one of `id`|`name`.
- `sortOrder`: Optional: sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$PORTAL_API_URL/v1/api-token" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Fri, 12 Jul 2019 17:22:46 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 530
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.15
Content-Range: items 1-9/9
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

[
  {
    "id": 2,
    "identity": "nwdev-api-key",
    "name": "nwdev-api-key"
  },
  {
    "id": 8,
    "identity": "test-api-token",
    "name": "test-api-token"
  },
  {
    "id": 9,
    "identity": "test-api-token",
    "name": "test-api-token"
  },

  . . .

]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
