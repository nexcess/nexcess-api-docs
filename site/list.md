# Portal: Site

## site:list
List Sites.

#### Access
service view

#### Input
- integer `filter[id]` (optional): filter list by system ID.
- string `filter[state]` (optional): filter list by state.
- string `filter[domain]` (optional): filter list by domain.
- string `filter[ip]` (optional): filter list by ip.
- string `filter[app_name]` (optional): filter list by app name.
- object `filter[cloud]` (optional): filter list by cloud.
- object `filter[cloudhost]` (optional): filter list by cloudhost.
- int `filter[package_id]` (optional): filter list by package_id.
- bool `filter[is_dev_account]` (optional): filter list by whether it is a dev account?
- bool `filter[is_staging_account]` (optional): filter list by whether it is a staging account?
- bool `filter[is_production_account]` (optional): filter list by whether it is a production account?
- int `filter[service_id]` (optional): filter list by service id.
- int `filter[parent_account_id]` (optional): filter list by parent account id.
- int `filter[reference_account_id]` (optional): filter list by refernce account id.
- string `filter[nickname]` (optional): filter list by nickname.
- int `filter[deploy_date]` (optional): filter list by deploy date.
- integer `match[id]` (optional): match against system ID.
- string `match[state]` (optional): match against token state.
- string `match[domain]` (optional): match against token domain.
- string `match[ip]` (optional): match against token ip.
- string `match[app_name]` (optional): match against app name.
- string `match[cloud]` (optional): match against cloud.
- string `match[cloudhost]` (optional): match against cloudhost.
- string `match[parent_account_id]` (optional): match against parent account id.
- string `match[reference_account_id]` (optional): match against reference account id.
- string `match[nickname]` (optional): match against nickname.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range.
- string `range[deploy_date]` (optional): find deploy dates within "{min}..{max}" range.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`state`|`ip`|`app`|`cloud`|`cloudhost`|`package`|`is_dev_account`|`is_staging_account`|`is_production_account`|`deploy_date`|`deploy_complete_date`|`parent_account`|`reference_account`|`client_domain`|`temp_domain`|`nickname`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl "$PORTAL_API_URL/v1/site" \
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
      "uri": "/v1/site/1091"
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
          "uri": "/v1/service/site/58378"
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
