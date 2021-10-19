# Portal: Address

## address:list
List Addresses.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
logged-in users

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/address" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
```

#### Responses
**Success Response** (request was accepted for processing): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 19 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/address
NocWorx-Api-Version: 0.0.0

{ "id": 1234, "identity": "Nexcess Staff" }"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
