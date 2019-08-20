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
  "id": 0,
  "identity": "ssh-key:delete (pending)",
  "status": "pending",
  "action": "ssh-key:delete",
  "request_date": 1566327634,
  "resource_uri": "",
  "staff_user": null,
  "user": { "id": 27767, "identity": "Annabel Whyman - user@nocworx.com" },
  "uuid": "f2805dd2-077e-44f9-8302-3a371c7d532d"
}

```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (doesn't exist on client account): 404 Not Found
