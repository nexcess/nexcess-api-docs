Admin: Creditcard
-----------------

**since** 0.5.0

creditcard:import
=================

Edits details of a client service.

Domains, Edgecast, Shared Hosting, Shared Resellers, Software Licenses, and VPS Services are currently not editable via this endpoint.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/service/{service_id}

**Parameters**:

- integer `service_id` (required): Serial id of the Service to edit
- boolean `auto_renew` (optional): Should the service renew automatically?
- string `override_price` (optional): Service monthly price
- string `pricing_type` (optional): Service pricing type; one of `monthly`|`yearly`
- integer `term` (optional): Service term, in months
- integer `turnup_day` (optional): Day service is billed

**Request**:
```
curl -i -X POST "$ADMIN_API_URL/v1/service/{service_id}" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "auto_renew": true,
    "override_price": "29.95",
    "term": 12
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
  "identity":"service:edit (pending)",
  "status":"pending",
  "action":"creditcard:import",
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
