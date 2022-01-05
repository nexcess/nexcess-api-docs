Portal: DataShares
------------------

**since** 0.3.0

datashare:open
==============

Opens a Datashare and retireves the secret data.

Note, this will increment the datashare "use" count. Once the datashare's expiration date has passed OR the maximum number of uses has been met, the datashare will expire and be deleted automatically.

**Endpoint**:  GET /v1/datashare/{uuid}/open

**Access**: logged-in users

**Parameters**: none

**Request**:
```
curl -i "$PORTAL_API_URL/v1/datashare/$DATASHARE_UUID/open" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 09 Jan 2020 16:32:09 GMT
Content-Type: application/json
Content-Length: 119
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
NocWorx-Api-Version: 0.2.0
Served-By: nwdev-web01-int

{
  "data": "SomeSuperSecretInformation",
  "datashare": {
    "id": 138,
    "identity": "",
    "metadata": {
      "scope": "datashare",
      "uri": "/v1/datashare/123e4567-e89b-12d3-a456-556642440000/"
    },
    "type": "client-secret"
  }
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (uuid doesn't exist on client account, or share has expired): 404 Not Found
