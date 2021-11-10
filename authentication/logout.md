# Portal: Authentication

## authentication:logout
Generate a new token with the extranet user removed and logout.

#### Access
authentication view

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/logout" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 10 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/logout
NocWorx-Api-Version: 0.0.0

[]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity
