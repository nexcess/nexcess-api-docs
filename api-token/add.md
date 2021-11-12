# Portal: Api Token

## api-token:add
Creates a new Api Token.

The new api token is returned in the response payload. This is the only time it will be accessible to the user; it will never be displayed again.

#### Access
logged-in users

#### Input
- string `name` (required): name for the new token; must contain a single line of text

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/api-token" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "name":"laptop"
  }'
```

#### Responses
**Success Response** (request was created for processing): 201 Created
```
HTTP/1.1 201 Created
Date: Tue, 02 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

{
  "id": 4,
  "identity": "Example, Inc.",
  "metadata": {
    "scope": "client-user-api-token",
    "uri": "/v1/api-token/4"
  },
  "name": "laptop",
  "token": "eyJ0eXAiOi ... veryLongAuthToken ..."
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
