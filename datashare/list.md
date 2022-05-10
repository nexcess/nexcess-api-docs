Portal: DataShares
------------------

**since** 0.3.0

datashare:list
==============

Lists datahsares that belong to the logged-in user, optionally filtering by the "owner" resource.

**Endpoint**:  GET /v1/datashare

**Alternate Endpoint**: GET /v1/datashare/{owner}/{owner_id}

**Alternate Endpoint**: GET /v1/datashare/ticket/{casenumber}

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
    "id": 210,
    "identity": "",
    "metadata": {
      "scope": "datashare",
      "uri": "/v1/datashare/268bdfa5-043a-41ea-b865-6087a1206fb6"
    },
    "expiration_date": 1641725936,
    "linked": {
      "id": 28,
      "identity": "Test Ticket Correct update7 (open)",
      "metadata": {
        "scope": "sf-ticket",
        "uri": "/v1/ticket/07770483"
      },
      "status": "open"
    },
    "max_uses": 10,
    "owner": {
      "id": 38116,
      "identity": "Howell Inc",
      "metadata": {
        "scope": "client",
        "uri": null
      },
      "status": "active"
    },
    "share_date": 1641380336,
    "type": "client-secret",
    "uses": 0,
    "uuid": "268bdfa5-043a-41ea-b865-6087a1206fb6"
  },
  
  . . .
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
