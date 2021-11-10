# Portal: Authentication

## authentication:login
Shows a time-limited Login token along with client and user data.

#### Access
authentication view

#### Input
- string `username` (required): Username of the user to login
- string `password` (required): password; must contain a single line of text

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/login" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 08 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/login
NocWorx-Api-Version: 0.0.0

{
  "authorization": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ2ZXIiOiIyIiwiaWF0IjoxNjM2MzY4MDA3LCJqdGkiOiIyYjgzNTkwYS04OTllLTQwOTctYjJlYy02YTU0YWY2OTc1MGYiLCJzdWIiOiJ7XCJleHRyYW5ldFwiOntcImNsaWVudFwiOjM4MTE0LFwidXNlclwiOjYxNDIwLFwicmVzdHJpY3Rpb25zXCI6W119fSIsImV4cCI6MTYzNjM3NTIwNywiYWx2IjoyfQ.EeSzRQ3L4aeHY2YNGfJSkT9cT0tsEnyuJdMLnRrMgKw",
  "user": {
    "id": 12345,
    "identity": "Nexcess Staff - support@nexcess.net",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/12345"
    }
  },
  "client": {
    "id": 12345,
    "identity": "Nexcess Staff",
    "status": "active",
    "metadata": {
      "scope": "client",
      "uri": null
    }
  }
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
