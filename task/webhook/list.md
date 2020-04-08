Portal: Webhook
---------------

**since** 0.5.0

webhook:list
============

Lists a client's stored webhooks.

**Endpoint**:  GET /v1/task/webhook

**Access**: account view permission

**Parameters**:
- integer `filter[name]` (optional): filter list by name
- integer `filter[resource]` (optional): filter list by the resource it listens to
- integer `filter[action]` (optional): filter list by the action it listens to
- integer `filter[url]` (optional): filter list by url
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `name`|`listen_to`|`url`
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$PORTAL_API_URL/v1/task/webhook" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 17 Jul 2019 01:50:28 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 1656
Vary: Accept-Encoding
X-Powered-By: PHP/7.4.2
Content-Range: items 1-5/5
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

[
  {
    "id": 14,
    "identity": "#14 example-webhook",
    "client": {
      "id": 12345,
      "identity": "Example, Inc.",
      "metadata": {
        "scope": "client",
        "uri": null
      }
    },
    "listen_to": {
      "resource": "cloud-server",
      "action": "reboot"
    },
    "metadata": {
      "scope": "api-webhook",
      "uri": "/v1/task/webhook/14/"
    },
    "name": "example-webhook",
    "url": "https://example.com/webhook"
  }

  . . .

]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
