# Portal: Address

## address:lookup-phone-number
Search phone number.

#### Access
address view

#### Input
- string `number` (required): phone number, in E.164 format

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/address/phone/{number}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
```

#### Responses
**Success Response** (request was accepted for processing): success
```
HTTP/1.1 success
Date: Mon, 19 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/address/phone/+18666392377
NocWorx-Api-Version: 0.0.0

{
  "callerName": null,
  "countryCode": "US",
  "phoneNumber": "+18666392377",
  "nationalFormat": "(866) 639-2377",
  "carrier": null,
  "addOns": null,
  "url": "https://lookups.twilio.com/v1/PhoneNumbers/+18666392377"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
