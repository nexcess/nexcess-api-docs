# Portal: Client

## client:list
Lists Client accounts that the authenticated user belongs to.

#### Access
logged-in users

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/client" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Thu, 11 Oct 2021 12:51:27 GMT
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 12345,
    "identity": "Bechtelar PLC",
    "status": "active",
    "company": {
      "id": 4,
      "identity": "Nexcess",
      "metadata": {
        "scope": "company",
        "uri": null
      }
    },
    "external_key": "",
    "external_key_prefix": null,
    "is_tax_exempt": false,
    "metadata": {
      "scope": "client",
      "uri": null
    },
    "name": "Bechtelar PLC",
    "owner": {
      "id": 61383,
      "identity": "Nexcess Staff - support@nexcess.net",
      "metadata": {
        "scope": "user",
        "uri": "/v1/user/12345"
      }
    },
    "self_classification": ""
  },
  
  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
