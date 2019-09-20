Admin: Client
-------------

**since** 0.2.0

client:add
==========

Creates a new Client account and its initial Client User (owner).

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

This documentation describes usage for a "company-use-only" Company (e.g., bearcats). Other usage will be documented at a later time.

**Endpoint**: POST /v1/client

**Parameters**:
- integer `company_id` (required): Serial id of the Company to add the new Client under
- boolean `company_use` (required): Is the client for company use? Must be set to `true`
- string `external_id` (required): Arbitrary client identifier (e.g., beyondhosting customer id)
- string `name` (required): A name for the Client account

**Request**:
```
curl -i -X POST "$ADMIN_API_URL/v1/client" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "company_id": "'"$COMPANY_ID"'",
    "company_use": true,
    "external_key": "'"$BEARCATS_CUSTOMER_ID"'",
    "name": "Bob Coleman"
  }'
```

**Success Response**:
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Thu, 19 Sep 2019 20:11:20 GMT
Content-Type: application/json
Content-Length: 245
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
Location: /v1/task/48d96192-8108-470b-9b4f-9275c312055e
NocWorx-Api-Version: 0.1.0
Served-By: nwdev-web01-int

{
  "id":134,
  "identity":"client:add (pending)",
  "status":"pending",
  "action":"client:add",
  "request_date":1568923879,
  "resource":null,
  "staff_user":{
    "id":1,
    "identity":"NocWorx Admin",
    "uri":null
  },
  "user":null,
  "uuid":"48d96192-8108-470b-9b4f-9275c312055e"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
