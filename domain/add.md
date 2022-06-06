# Portal: Domain

## domain:add

Orders a new domain registration and an associated Service.

Add requests are queued, meaning they will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
Order Edit permissions

#### Input
- string `nickname` (optional): A customer-chosen identifier for the Order.
- string `discount_code` (optional: A Discount to apply to the Order.
- int `package_id` (optional): If omitted, Package will be determined by the domain TLD.
- int `term` (required): The purchase term (in months).
- array[] `addons` (optional): A list of Package Addons to order:
  - int `addon_id` (required): The system ID of the Addon.
  - int `quantity` (required): The quantity of Addons to add to the Order.
- string `domain_name` (required): The domain name, with or without TLD, to order.
- int `tld_id` (required if `domain_name` omits TLD): The system ID of the TLD to order.
- array[] `contact` (optional): Whois Contact information to use. If omitted, the Client's "technical" contact information will be used. _see address:add inputs._

#### Request
```
$ curl -X POST "$PORTAL_API/v1/domain" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "domain_name": "example.horse",
    "term": 12,
    "contact": {
      "technical": {
        "first_name":"William",
        "last_name":"Louis",
        "address1":"21700 Melrose Ave",
        "country":"US",
        "state":"MI",
        "zip":"48075",
        "city":"Southfield",
        "email":"william@example.com"
      }
    }
  }'
```

#### Responses
**Success Response** (accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Thu, 25 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 144
Location: /v1/cloud-account/1091/nickname
NocWorx-Api-Version: 0.6.0

{
  "id": 487,
  "identity": "domain:add (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/8fbf4c8c-fd55-49e6-a2c7-54db51b27be7"
  },
  "status": "pending",
  "action": "domain:add",
  "api_version": "0.6.0",
  "errors": {},
  "input": {},
  "request_date": 1637833711,
  "resolved_date": null,
  "resource": null,
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Example, Inc - alice@example.com",
    "metadata": {
        "scope": "user",
        "uri": "/v1/user/61420"
    }
  },
  "uuid": "8fbf4c8c-fd55-49e6-a2c7-54db51b27be7"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity
