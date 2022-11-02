# Portal: Site

## site:change-php-version
Changes PHP versions installed on the Site, optionally first checking compatibility with the installed app.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
service edit

#### Input
- integer `id` (required): System ID of the Site to edit
- string `php_version` (required): php version; Target PHP version.
- bool `skip_compatibility_check` (optional): skip the app compatibility check?

#### Request
```
$ curl -X POST "$PORTAL_API_URL/v1/site/{id}/php-version" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "php_version":"7.2",
    "skip_compatibility_check":"false"
  }'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Mon, 15 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/site/1091/php-version
NocWorx-Api-Version: 0.0.0

{
  "id": 483,
  "identity": "site:change-php-version (pending)",
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/2d9a1ca5-7eb1-4f64-bc03-ceee39731f21"
  },
  "status": "pending",
  "action": "site:change-php-version",
  "api_version": "0.5.0",
  "errors": {},
  "input": {},
  "request_date": 1637761022,
  "resolved_date": null,
  "resource": {
    "id": 1091,
    "identity": "39869b24b8.1700.lwdns.dev",
    "metadata": {
      "scope": "virt-guest-cloudaccount",
      "uri": "/v1/site/1091"
    },
    "status": "used",
    "state": "stable",
    "type": "account"
  },
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Example, Inc - alice@example.com",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
      }
  },
  "uuid": "2d9a1ca5-7eb1-4f64-bc03-ceee39731f21"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity
