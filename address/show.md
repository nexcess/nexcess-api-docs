# Portal: Address

## address:show
Show Address details.

#### Access
address view

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/address/{id}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
```

#### Responses
**Success Response** (request was accepted for processing): success
```
HTTP/1.1 success
Date: Mon, 19 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/address/1234
NocWorx-Api-Version: 0.0.0

{
  "id": 73402,
  "identity": "first name last name",
  "address1": "21700 Melrose Ave",
  "address2": "21700 Melrose Ave",
  "cell": "",
  "city": "Southfield",
  "company": "",
  "country": "US",
  "email": "test@gmail.com",
  "fax": "",
  "first_name": "first name",
  "is_residence": 1,
  "last_name": "last name",
  "metadata": {
    "scope": "address",
    "uri": "/v1/address/73402"
  },
  "phone": "234234",
  "state": "MI",
  "type": "billing",
  "zip": "48075"
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
