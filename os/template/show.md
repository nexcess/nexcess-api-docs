Portal: Os Templates
--------------------

**since** 0.2.0

os-template:show
================

Shows details of an operating system installation template.

**Endpoint**:  GET /v1/os-template/{template_id}

**Access**: order view permission

**Parameters**: none

**Request**:
```
curl -i "$PORTAL_API_URL/v1/os-template/$TEMPLATE_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 22 Oct 2019 12:53:01 GMT
Content-Type: application/json
Content-Length: 61
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
NocWorx-Api-Version: 0.2.0
Served-By: nwdev-web01-int

{ "id": 4, "identity": "CentOS 7 x64", "uri": "/v1/os-template/4/" }
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (token_id doesn't exist on your account (or at all)): 404 Not Found
