# Portal: Task

## task:show
Shows Task details.

#### Access
logged-in users

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/task/{TASK_ID}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Tue, 04 Jan 2022 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

{
  "id": 445,
  "identity": "address:add (success)",
  "status": "success",
  "action": "address:add",
  "api_version": "0.5.0",
  "errors": [],
  "input": {
    "address1": "21700 Melrose Ave",
    "address2": "21700 Melrose Ave",
    "city": "Southfield",
    "state": "MI",
    "country": "US",
    "zip": "48075",
    "type": "billing",
    "company": null,
    "first_name": "first name",
    "last_name": "last name",
    "email": "alice@example.com",
    "phone": "234234",
    "cell": null,
    "fax": null
  },
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/7a6a9390-972b-4583-97ac-7240120b96d4/"
  },
  "request_date": 1634637796,
  "resolved_date": 1634637799,
  "resource": null,
  "staff_user": null,
  "user": {
    "id": 61420,
    "identity": "Alice Bowman - alice@example.com",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420/"
    }
  },
  "uuid": "7a6a9390-972b-4583-97ac-7240120b96d4"
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
