Portal: Authentication
----------------------

**since** 0.0.0

auth:login
==========

Client user authentication with a username and password.

A successful response includes a time-limited Bearer token to be included in the `Authorization` header on subsequent requests.

This endpoint is mainly intended for use by web applications, which would store the token for use during the user's logged-in session. (When the token expires, requests will recieve 401 responses.) For general API usage, an api token should be used instead. @see api-token:add

Endpoint:  POST /v1/login

**Access**: public

**Parameters**:
- `username`: Required: email address of the user to log in as.
- `password`: Required: user's password.
- `code`: Optional: 2FA code where enabled/required by client settings.
- `client_id`: Optional: ID of client account to log in as.
  Users can belong to more than one client account.
  If not specified, logs in as the most recently logged-in client.

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/login" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{ "username": "user@example.com", "password": "KlaatuBaradaNikto" }'
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Thu, 11 Jul 2019 19:10:17 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 364
X-Powered-By: PHP/7.2.15
Authorization: Bearer eyJ0eXAiOiJKV1QiL . . . very long auth token
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "authorization": "eyJ0eXAiOiJKV1QiL . . . very long auth token",
  "user": { "id": 27767, "identity": "Annabel Whyman - user@nocworx.com" },
  "client": { "id": 24512, "identity": "Bosco-Bradtke" }
}
```

**Failure Response** (wrong user/pass): 401 Unauthorized

**Failure Response** (user cannot log in as requested client): 403 Forbidden
