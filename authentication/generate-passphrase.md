# Portal: Authentication

## authentication:generate-passphrase
Shows generated passphrase/password.

#### Access
authentication view

#### Input
- integer `length` (optional): length of the password to generate; within "{min}..{max}" length.
- integer `words` (optional): words of the password to generate.

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/passphrase" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 10 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/passphrase
NocWorx-Api-Version: 0.0.0

{
  "feedback": {
    "warning": "",
    "suggestions": []
  },
  "passphrase": "MuzzleSandyEthicGlides",
  "score": 4,
  "time_to_crack": {
    "online_throttling_100_per_hour": "centuries",
    "online_no_throttling_10_per_second": "centuries",
    "offline_slow_hashing_1e4_per_second": "centuries",
    "offline_fast_hashing_1e10_per_second": "12 years"
  }
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

