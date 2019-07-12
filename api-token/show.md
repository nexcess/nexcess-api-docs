Portal: Api Tokens
------------------

**since** 0.0.0

api-token:show
==============

Shows an api token.

**Endpoint**:  GET /v1/api-token

**Access**: logged-in users

**Parameters**: none

**Request**:
```
curl -i "$PORTAL_API_URL/v1/api-token/$TOKEN_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Fri, 12 Jul 2019 19:24:32 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 49
X-Powered-By: PHP/7.2.15
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 14,
  "identity": "chuck",
  "name": "chuck"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (token_id doesn't exist on your account (or at all)): 404 Not Found
