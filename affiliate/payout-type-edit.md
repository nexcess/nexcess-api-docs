# Portal: Affiliate

## address:edit
Edit Affiliate Client payout type

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
affiliate payout type edit

#### Input
- integer `id` (required): System ID of the Affiliate to edit
- string `payout_type` (optional): payout type; one of `cash`|`check`|`credit`|`paypal`|`wire`|`other`

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/affiliate/payout-type" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "id":"1234",
    "payout_type":"credit"
  }'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Mon, 19 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/affiliate/payout-type
NocWorx-Api-Version: 0.0.0

{ "id": 1234, "identity": " (pending)" }"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (invalid inputs): 422 Unprocessable Entity

