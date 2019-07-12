User
----

user:self
=========

Shows information about the currently-authenticated client user.

Endpoint:  GET /v1/user/self

Access: Bearer token

Parameters: none

Request:
```
curl -i "$PORTAL_API_URL/v1/user/self" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

Success Response:
```
HTTP/1.1 200 OK
Server: nginx
Date: Fri, 12 Jul 2019 13:13:40 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 1751
X-Powered-By: PHP/7.2.15
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "user": {
    "id": 27767,
    "identity": "Annabel Whyman - user@nocworx.com",
    "first_name": "Annabel",
    "last_name": "Whyman",
    "activated": true,
    "beta_tester": false,
    "email": "user@nocworx.com",
    "verified": true,
    "status": "active",
    "client": { "id": 24512, "identity" : "Bosco-Bradtke" },
    "is_owner": true,
    "roles":[
      { "id": 34050, "identity": "Superuser" },
      { "id": 34051, "identity": "Billing" },
      { "id": 34052, "identity": "Technical" }
    ],
    "access": {
      "area": "extranet",
      "company": { "id": 4, "identity": "Nexcess" },
      "locked": false,
      "login_enable_date": 1559822176
    }
  },
  "password": {
    "expired": true,
    "expires_in": 0
  },
  "permissions": {
    "ACCOUNT": 6,
    "USERS": 7,
    "USER-ROLES": 7,
    "ADDRESSES": 7,
    "TICKETS": 6,
    "INVOICES": 4,
    "PAYMENTS": 6,
    "CREDITS": 4,
    "ORDERS": 6,
    "CREDITCARDS": 7,
    "AFFILIATE-SETTINGS": 7,
    "SERVICES": 7,
    "DNS": 7,
    "BILLING": 4,
    "TECHNICAL": 4,
    "PUBLIC": 7
  },
  "settings": {
    "client-user.pagination.perpage": "25",
    "client-user.login.alert.unknown-device": "1",
    "client-user.login.password-blacklist": "qwertyasdfzxcvbn\r\ncorrecthorsebatterystaple\r\nnexcess\r\nthermo",
    "client-user.login.password-check-history": "0",
    "client-user.login.password-expires": "0",
    "client-user.login.password-strength": "3",
    "feedback_department": null,
    "perfectaudience": null
  },
  "resources": {
    "knowledgebase": { "name": "Knowledge Library", "link": null },
    "git_access_tokens": [
      {"id":1,"identity":""},
      {"id":2,"identity":""},
      {"id":3,"identity":""}
    ]
  }
}
```
_note, some of the above items, particularly "settings" and "resources", may vary from user to user._
_this payload may change before the api is released._

Failure Response (unauthorized): 401 Unauthorized
