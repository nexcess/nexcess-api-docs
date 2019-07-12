Portal: Api Tokens
------------------

**since** 0.0.0

api-token:add
=============

Creates a new api token.

The new api token is returned in the response payload. This is the only time it will be accessible to the user; it will never be displayed again.

**Endpoint**:  POST /v1/api-token

**Access**: logged-in users

**Parameters**:
- `name`: Required: an identifier for the new token.

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/api-token" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{ "name": "chuck" }'
```

**Success Response**: 201 Created
```
HTTP/1.1 201 Created
Server: nginx
Date: Fri, 12 Jul 2019 17:10:06 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 281
X-Powered-By: PHP/7.2.15
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 16,
  "identity": "chuck",
  "name": "chuck",
  "token": "eyJ0eXAiOiJKV1QiL . . . very long auth token"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (missing/bad input): 422 Unprocessable Entity
```
HTTP/1.1 422 Unprocessable Entity
Server: nginx
Date: Fri, 12 Jul 2019 17:12:36 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 101
X-Powered-By: PHP/7.2.15
Served-By: nwdev-web01-int

{
  "message": "Unprocessable Entity",
  "errors": [
    { "message": "This input is required", "reference": "name" }
  ]
}
```
