Portal: Ssh Keys
----------------

**since** 0.0.0

ssh-key:add
===========

Creates a new ssh key.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**:  POST /v1/api-token

**Access**: logged-in users

**Parameters**:
- `name`: Required: an identifier for the new token.

**Request**:
```
curl -i -X POST "$PORTAL_API_URL/v1/ssh-key" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{ "name": "example-key", "key": "'"$SSH_KEY"'" }'
```

**Success Response**: 201 Created
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Tue, 20 Aug 2019 18:55:07 GMT
Content-Type: application/json
Content-Length: 260
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
Location: /v1/task/6bf71868-d4ea-486a-95b9-0576ad3ef984
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 0,
  "identity": "ssh-key:add (pending)",
  "status": "pending",
  "action": "ssh-key:add",
  "request_date": 1566327307,
  "resource_uri": "",
  "staff_user": null,
  "user": { "id": 27767, "identity": "Annabel Whyman - user@nocworx.com" },
  "uuid": "6bf71868-d4ea-486a-95b9-0576ad3ef984"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (missing/bad input): 422 Unprocessable Entity
