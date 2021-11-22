# Portal: App

## app:show
Shows App details.

#### Access
app view

#### Request
```
$ curl "$PORTAL_API_URL/v1/app/{id}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Thu, 28 Oct 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/app/1234
NocWorx-Api-Version: 0.0.0

{
    "id": 19,
    "identity": "BigCommerce for WordPress 1",
    "status": "active",
    "is_core_upgradable": true,
    "is_developerable": false,
    "is_installable": true,
    "is_plugin_upgradable": true,
    "is_wordpress_based": true,
    "metadata": {
      "scope": "app-app",
      "uri": "/v1/app/19"
    },
    "minimum_php_version": "5.6.20",
    "name": "BigCommerce for WordPress",
    "type": "bigcommerce",
    "version": "1"
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
