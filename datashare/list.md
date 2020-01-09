Portal: DataShares
------------------

**since** 0.3.0

datashare:list
==============

Lists datahsares that belong to the logged-in user, optionally filtering by the "owner" resource.

**Endpoint**:  GET /v1/datashare

**Alternate Endpoint**: GET /v1/datashare/{owner}/{owner_id}

This alternate endpoint is sugar for GET /v1/datashare?filter[owner]={owner}&filter[owner_id]={owner_id} and will serve identical responses.

**Access**: logged-in users

**Parameters**:
- `filter[uuid]`: (optional): filters results by datashare uuid.
- `filter[owner]`: (optional): filters results by owner object scope.
- `filter[owner_id]`: (required if using `filter[owner]`): filters results by owner object id.
- `page`: (optional): 1-based result set count for paginated results.
- `pageSize`: (optional): maximum number of results to include per "page" of a paginated list.
- `sortBy`: (optional): field to sort the list by; one of `uuid`|`owner`|`owner_id`.
- `sortOrder`: (optional): sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$PORTAL_API_URL/v1/datashare/$OWNER_SCOPE/$OWNER_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 09 Jan 2020 16:29:24 GMT
Content-Type: application/json
Content-Length: 284
Content-Range: items 1-1/1
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
NocWorx-Api-Version: 0.3.0
Served-By: nwdev-web01-int

[
  {
    "id": 138,
    "identity": "",
    "max_uses": 10,
    "metadata": {
      "scope": "datashare",
      "uri": "/v1/datashare/123e4567-e89b-12d3-a456-556642440000/"
    },
    "owner": {
      "id": 58401,
      "identity": "us-midwest-1 - example.com - 203.113.0.1",
      "metadata": {
        "scope": "service",
        "uri": null
      }
    },
    "type": "ssh-password",
    "uses": 0,
    "uuid": "123e4567-e89b-12d3-a456-556642440000"
  },

  . . .
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
