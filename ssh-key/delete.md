Portal: Ssh Keys
----------------

**since** 0.0.0

ssh-key:delete
==============

Deletes an ssh key.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**:  DELETE /v1/ssh-key/{token_id}

**Access**: logged-in users

**Parameters**: none

**Request**:
```
curl -i -X DELETE "$PORTAL_API_URL/v1/ssh-key/$KEY_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Tue, 20 Aug 2019 19:00:35 GMT
Content-Type: application/json
Content-Length: 266
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
Location: /v1/task/f2805dd2-077e-44f9-8302-3a371c7d532d
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 520,
  "identity": "ssh-key:delete (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/88180f55-682f-48e6-b1e4-71fe1964eb5b"
  },
  "status": "pending",
  "action": "ssh-key:delete",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1638436250,
  "resolved_date": null,
  "resource": {
    "id": 140,
    "identity": "example-key - SHA256:3XTUdV3yYM/. . . (RSA)",
    "metadata": {
      "scope": "user-ssh-key",
      "uri": "/v1/ssh-key/140"
    }
  },
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Annabel Whyman - user@nocworx.com",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  },
  "uuid": "88180f55-682f-48e6-b1e4-71fe1964eb5b"
}

```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (doesn't exist on client account): 404 Not Found
