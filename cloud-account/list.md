# Portal: Cloud Account

## cloud-account:list
List Cloud Accounts.

#### Access
service view

#### Request
```
$ curl "$PORTAL_API_URL/v1/cloud-account" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Tue, 16 Nov 2021 12:51:27 GMT
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 1091,
    "identity": "39869b24b8.1700.lwdns.dev",
    "metadata": {
      "scope": "virt-guest-cloudaccount",
      "uri": "/v1/cloud-account/1091"
    },
    "app": {
      "id": 20,
      "identity": "WordPress 5",
      "metadata": {
        "scope": "app-app",
        "uri": "/v1/app/20"
      },
      "status": "active",
      "is_core_upgradable": true,
      "is_developerable": true,
      "is_installable": true,
      "is_plugin_upgradable": true,
      "is_wordpress_based": true,
      "minimum_php_version": "5.6.20",
      "name": "WordPress",
      "type": "wordpress",
      "version": "5"
    },
      "can_modify_domain": true,
      "client_domain": "",
      "cloud": {
        "id": 4,
        "identity": "us-midwest-2",
        "metadata": {
          "scope": "virt-cloud",
          "uri": null
        },
        "status": "active",
        "type": "openstack"
      },
      "deploy_date": 1629292333,
      "dev_account_count": 0,
      "domain": "39869b24b8.1700.lwdns.dev",
      "ip": "192.190.222.73",
      "is_dev_account": false,
      "is_domain_agnostic": true,
      "is_staging_account": false,
      "nickname": "",
      "package": {
        "id": 761,
        "identity": "Spark",
        "metadata": {
          "scope": "package",
          "uri": "/v1/package/761"
        },
        "status": "web-active",
        "type": "virt-guest-cloud"
      },
      "parent_account": null,
      "reference_account": null,
      "screenshot_url": "https://objects.liquidweb.services/mirador-stg/site/38114/virt-guest-cloudaccount-1091/36ab0548-110b-4b7e-ab15-521584409102.png",
      "service": {
        "id": 58378,
        "identity": "WordPress Spark Plan",
        "metadata": {
          "scope": "service",
          "uri": "/v1/service/cloud-account/58378"
        },
        "status": "enabled",
        "state": "stable",
        "type": "virt-guest-cloud"
      },
      "staging_account_count": 0,
      "state": "stable",
      "temp_domain": "39869b24b8.1700.lwdns.dev"
    },

  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
