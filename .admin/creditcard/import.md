Admin: Creditcard
-----------------

**since** 0.5.0

creditcard:import
=================

Creates a new Creditcard record and imports its auth token.

This is intended primarily for use in migrations, where a customer from an acquired company might already have creditcard info stored with a payment gateway. Currently, only authorize.net accounts are supported.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/creditcard/import

**Parameters**:

- integer `client_id` (required): Serial id of the Client to import the new card under
- string `name` (optional): User-provided nickname for the card
- integer `expiration` (required): Expiration date (unixtime)
- integer `gateway_id` (required): Serial id of the payment gateway to import the card to
- string `last_digits` (required): Last four digits of the card number
- string `payment_gateway` (required): Identifier for target payment gateway type. Currently, only `authorize.net` is supported
- string `payment_profile_id` (required when `payment_gateway`=`authorize.net`): The auth.net "customerPaymentProfileId"
- string `profile_id` (required when `payment_gateway`=`authorize.net`): The auth.net "customerProfileId"
- string `type` (required): Creditcard issuer; one of `MasterCard`|`Visa`|`American Express`|`Discover`

**Request**:
```
curl -i -X POST "$ADMIN_API_URL/v1/creditcard/import" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "client_id": "'"$CLIENT_ID"'",
    "name": "My Favorite Card",
    "type": "MasterCard",
    "expiration": 1594904123,
    "gateway_id": 12,
    "last_digits": "6789",
    "payment_gateway": "authorize.net",
    "profile_id": "'"$PROFILE_ID"'",
    "payment_profile_id": "'"$PAYMENT_PROFILE_ID"'",
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
  "identity":"creditcard:import (pending)",
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

**Failure Response** (invalid inputs, unsupported payment gateway): 422 Unprocessable Entity
