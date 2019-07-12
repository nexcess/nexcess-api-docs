Portal: Api Tokens
------------------

**since** 0.0.0

api-token:delete
================

Deletes an api token.

Delete requests are queued, meaning they will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a `Location` header that can be polled to determine the status of the task. @see task:show.

**Endpoint**:  DELETE /v1/api-token/{token_id}

**Access**: logged-in users

**Parameters**: none

**Request**:
```
curl -i -X DELETE "$PORTAL_API_URL/v1/api-token/$TOKEN_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 202 Accepted
```HTTP/1.1 202 Accepted
Server: nginx
Date: Fri, 12 Jul 2019 19:35:31 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 270
X-Powered-By: PHP/7.2.15
Location: /v1/task/887db804-d8af-4daf-82a0-4a9b125d7b56
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 0,
  "identity": "api-token:delete (pending)",
  "uuid": "887db804-d8af-4daf-82a0-4a9b125d7b56",
  "action": "api-token:delete",
  "status": "pending",
  "request_date": 1562960130,
  "resource_uri": "",
  "staff_user": null,
  "user": { "id": 27767, "identity": "Annabel Whyman - user@nocworx.com" }
}


```
_some fields on this payload may change before the Api is released._

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (token_id doesn't exist on your account (or at all)): 404 Not Found
