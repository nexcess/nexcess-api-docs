# Portal: Authentication

## authentication:login
Shows guessed passphrase/password.

#### Access
authentication view

#### Input
- string `passphrase` (required): guess passphrase; within "{min}..{max}" length.

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/assess-passphrase" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 10 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/assess-passphrase
NocWorx-Api-Version: 0.0.0

{
  "feedback": {
    "warning": "",
    "suggestions": []
  },
  "passphrase": "test@12345",
  "score": 3,
  "time_to_crack": {
    "online_throttling_100_per_hour": "centuries",
    "online_no_throttling_10_per_second": "3 years",
    "offline_slow_hashing_1e4_per_second": "23 hours",
    "offline_fast_hashing_1e10_per_second": "less than a second"
  }
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity
