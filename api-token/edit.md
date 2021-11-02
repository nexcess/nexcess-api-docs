# Portal: Api Token

## api-token:edit
Edits a stored Api Token.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
api-token edit

#### Input
- integer `id` (required): System ID of the Api Token to edit
- string `name` (required): name; must contain a single line of text

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/api-token" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "id":"4",
    "name":"Example, Inc"
  }'
```

#### Responses
**Success Response** (request was created for processing): 201 Created
```
HTTP/1.1 201 Created
Date: Tue, 02 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/api-token
NocWorx-Api-Version: 0.0.0

{
  "id": 5,
  "identity": "Example1, Inc.",
  "metadata": {
    "scope": "client-user-api-token",
    "uri": "/v1/api-token/4"
  },
  "name": "Example1, Inc.",
  "token": "eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ2ZXIiOiIyIiwiaWF0IjoxNjM1ODUwMDA3LCJqdGkiOiIzYzAzNjE0NS1iYjE0LTRlZjAtOWIwNy1mN2JkNWU4NDEwYmQiLCJzdWIiOiJ7XCJleHRyYW5ldFwiOntcImNsaWVudFwiOjM4MTE0LFwidXNlclwiOjYxNDIwLFwidG9rZW5faWRcIjo0fX0iLCJhbHYiOjN9._nxUX7XYVX-LJYSuFEdRgpKZnaKcMMzRsIY5o4MazzI"
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
