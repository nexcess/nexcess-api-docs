Portal: Api Tokens
------------------

**since** 0.0.0

api-token:show
==============

Edits an api token.

Edit requests are queued, meaning they will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a `Location` header that can be polled to determine the status of the task. @see task:show.

**Endpoint**:  POST /v1/api-token/{token_id}

**Access**: logged-in users

**Parameters**:
- `name`: Required: new name for the token.

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/api-token/$TOKEN_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json" \
  -d '{ "name": "charles" }'
```

**Success Response**: 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Fri, 12 Jul 2019 19:28:17 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 266
X-Powered-By: PHP/7.2.15
Location: /v1/task/34595a2b-40b8-4021-9f0d-6f3e96c8462a
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 0,
  "identity": "api-token:edit (pending)",
  "uuid": "34595a2b-40b8-4021-9f0d-6f3e96c8462a",
  "action": "api-token:edit",
  "status": "pending",
  "request_date": 1562959696,
  "resource_uri": "",
  "staff_user": null,
  "user": { "id": 27767, "identity": "Annabel Whyman - user@nocworx.com" }
}
```
_some fields on this payload may change before the Api is released._

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (token_id doesn't exist on your account (or at all)): 404 Not Found
