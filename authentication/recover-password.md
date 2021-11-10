# Portal: Authentication

## authentication:recover-password
Handles the lost password reset process.

#### Access
authentication view

#### Input
- integer `request_id` (required): System request ID of the authentication to recover password.
- string `code` (required): code for password recovery.
- string `two_factor_code` (optional): two factor code for password recovery.
- string `password` (required): authenticated user password.

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/recover-password" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 10 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/recover-password
NocWorx-Api-Version: 0.0.0

{
  "activated": true,
  "is_beta_tester": true
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity
