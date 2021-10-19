# Portal: Address

## address:lookup-phone-number
Search phone number.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
logged-in users

#### Input
- string `number` (required): phone number; must contain digit

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/address/phone/{number}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "number":"234234"
  }'
```

#### Responses
**Success Response** (request was accepted for processing): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 19 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/address/phone/234234
NocWorx-Api-Version: 0.0.0

{ "number": 234234, "identity": "address:phone (pending)" }"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
