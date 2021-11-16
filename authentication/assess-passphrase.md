# Portal: Authentication

## authentication:assess-passphrase
Shows information about passphrase complexity and estimated time-to-crack.

#### Access
anyone

#### Input
- string `passphrase` (required): passphrase to assess; within 12 - 72 bytes in length.

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/assess-passphrase/$PASSWORD" \
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
  "passphrase": "theamazingpassphraseyouchose",
  "score": 4,
  "time_to_crack": {
    "online_throttling_100_per_hour": "centuries",
    "online_no_throttling_10_per_second": "centuries",
    "offline_slow_hashing_1e4_per_second": "centuries",
    "offline_fast_hashing_1e10_per_second": "7 days"
  }
}
```

**Failure Response** (other bad input): 422 Unprocessable Entity
