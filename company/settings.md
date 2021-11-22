# Portal: Company

## company:settings
Show company settings.

#### Access
Company settings view permissions

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/company/settings" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Tue, 16 Jul 2019 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/attachment/54/download-link
NocWorx-Api-Version: 0.0.0

{
    "id": 4,
    "identity": "Nexcess",
    "affiliate_enabled": true,
    "beta": {
        "aws": false
    },
    "captcha_enabled": {
        "login": false,
        "register": false
    },
    "feedback_enabled": false,
    "google_analytics": null,
    "label": "nexcess",
    "metadata": {
        "scope": "company",
        "uri": null
    },
    "name": "Nexcess",
    "register_enabled": true,
    "support_department": 1,
    "two_factor_enabled": false
}

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
