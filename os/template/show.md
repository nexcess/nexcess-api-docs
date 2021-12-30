# Portal: Os Template

## os template:show
Show Operating System install template details.

#### Access
os template view

#### Request
```
$ curl "$PORTAL_API_URL/v1/os-template/$TEMPLATE_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Thu, 30 Dec 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/os-template/1234
NocWorx-Api-Version: 0.0.0

{
  "id": 3,
  "identity": "CentOS 6 x64",
  "status": "web-active",
  "metadata": {
    "scope": "operating-system-install-template",
    "uri": "/v1/os-template/3/"
  }
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
