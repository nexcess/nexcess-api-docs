# Portal: Api Token

## api-token:show
Shows Api Token details.

#### Access
api-token view

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/api-token/{id}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Tue, 02 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/api-token/2
NocWorx-Api-Version: 0.0.0

{
  "id": 2,
    "identity": "Example, Inc.",
    "metadata": {
      "scope": "client-user-api-token",
      "uri": "/v1/api-token/2"
    },
    "name": "Example, Inc".
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
