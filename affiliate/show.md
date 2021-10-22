# Portal: Affiliate

## affiliate:show
Show Affiliate details.

#### Access
affiliate view

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/affiliate" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
```

#### Responses
**Success Response** (request was accepted for processing): 200 OK
```
HTTP/1.1 200 OK
Date: Fri, 22 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/affiliate
NocWorx-Api-Version: 0.0.0

{
  "id": 38114,
  "identity": "Neeru 1 Api Testing",
  "is_affiliate": false,
  "metadata": {
    "scope": "client",
    "uri": null
  }
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
