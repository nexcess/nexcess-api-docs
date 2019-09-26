Admin: Clients
--------------

**since** 0.2.0

client:list
===========

Lists Client accounts.

**Endpoint**:  GET /v1/client

**Alternate Endpoint**: GET /v1/client/{status}

This alternate endpoint is sugar for `?filter[status]={status}` and will return identical responses.

**Alternate Endpoint**: GET /v1/client/{company_id}-{external_key}

This alternate endpoint is sugar for `?filter[company_id]={company_id}&filter[external_key]={external_key}` and will return identical responses.

**Access**: client view permission

**Parameters**:
- integer `filter[company_id]`: (required if using `filter[external_key]`): filter list by company
- string `filter[external_key]`: (optional): filter list by account identifier
- boolean `filter[has_agent]`: (optional): filter list by whether the client has an associated staff user
- integer `filter[has_agent]`: (optional): filter list by associated staff user serial id
- string `filter[status]`: (optional): filter list by account status; one of `active`|`inactive`|`suspended`|`fraud`|`pending`
- integer `filter[owner_id]`: (optional): filter list by owner's serial id
- integer `page`: (optional): 1-based result set count for paginated results.
- integer `pageSize`: (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy`: (optional): field to sort the list by; one of `external_key`|`id`|`company_id`|`status`
- string `sortOrder`: (optional): sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$ADMIN_API_URL/v1/client" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 26 Sep 2019 11:42:27 GMT
Content-Type: application/json
Content-Length: 6335
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.21
Content-Range: items 1-25/24537
NocWorx-Api-Version: 0.1.0
Served-By: nwdev-web01-int

[
  {
    "id": 13255,
    "identity": "Mayer Inc",
    "status": "active",
    "company": {
      "id": 4,
      "identity": "Nexcess",
      "uri": null
    },
    "external_key": "",
    "has_agent": false,
    "name": "Mayer Inc",
    "open_tickets": [],
    "owner": {
      "id": 24,
      "identity": "Mireille Huel - gerlach.buster@example.org",
      "uri": null
    },
    "services": [
      {
        "id": 25761,
        "identity": "DS-410 - 203.0.113.1 - asdf.example.com",
        "uri": null
      }
    ]
  },

  . . .

]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
