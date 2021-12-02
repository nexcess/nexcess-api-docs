Portal: Ssh Keys
----------------

**since** 0.0.0

ssh-key:add
===========

Creates a new ssh key.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**:  POST /v1/ssh-key

**Access**: logged-in users

**Parameters**:
- `name`: Required: an identifier for the key
- `key`: Required: the public key

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
  "id": 519,
  "identity": "ssh-key:add (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/bd369617-6f42-43cd-9edd-037bea67d6ad"
  },
  "status": "pending",
  "action": "ssh-key:add",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1638435978,
  "resolved_date": null,
  "resource": null,
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Nexcess Staff - nocworx-dev@nexcess.net",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  },
  "uuid": "bd369617-6f42-43cd-9edd-037bea67d6ad"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (missing/bad input): 422 Unprocessable Entity
