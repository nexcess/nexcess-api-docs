# Portal: Cloud Account

## cloud-account:set-nickname
Change the nickname of a cloud account

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
cloud account edit

#### Input
- integer `id` (required): System ID of the cloud account to edit
- string `nickname` (required): nickname; nickname of the cloudaccount.

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/cloud-account/{id}/nickname" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "nickname":"7.2",
  }'
``` 
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Thu, 25 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/cloud-account/1091/nickname
NocWorx-Api-Version: 0.0.0

{
  "id": 487,
  "identity": "cloud-account:set-nickname (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/8fbf4c8c-fd55-49e6-a2c7-54db51b27be7"
  },
  "status": "pending",
  "action": "cloud-account:set-nickname",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1637833711,
  "resolved_date": null,
  "resource": {
    "id": 1091,
    "identity": "39869b24b8.1700.lwdns.dev",
    "metadata": {
      "scope": "virt-guest-cloudaccount",
      "uri": "/v1/cloud-account/1091"
    },
    "status": "used",
    "state": "stable",
    "type": "account"
  },
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Example, Inc - support@nexcess.net",
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

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
