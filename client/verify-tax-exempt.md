# Portal: Client

## client:verify-tax-exempt
Shows verified tax exempt details

#### Access
client view

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/client/tax-exempt/{number}/{country}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Thu, 11 Oct 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/client/tax-exempt/X1234567890/US
NocWorx-Api-Version: 0.0.0

{
  "number": "X1234567890",
  "verified": "true"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
