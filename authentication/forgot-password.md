# Portal: Authentication

## authentication:forgot-password
Creates a password reset request. Initialize, store, and send email.

#### Access
authentication view

#### Input
- string `username` (required): username of the user; in email format.

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/forgot-password" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 10 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/forgot-password
NocWorx-Api-Version: 0.0.0

[]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

