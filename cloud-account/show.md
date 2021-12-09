# Portal: Api Token

## api-token:show
Show Cloud Account details.

#### Access
service view

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/cloud-account/{CLOUDACCOUNT_ID}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Tue, 02 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

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
  "cloudhost": {
    "id": 34100,
    "identity": "jarvis01-dev-kvm10.p01s02.lan3.us-midwest-2 - cloudhost-1700044887.us-midwest-2.lwdns.dev",
    "metadata": {
      "scope": "virt-guest",
      "uri": "/v1/cloud-server/34100"
    },
    "status": "used",
    "type": "kvm"
  },
  "deploy_complete_date": 1629292369,
  "deploy_date": 1629292333,
  "dev_account_count": 0,
  "domain": "39869b24b8.1700.lwdns.dev",
  "environment": {
    "software": {
      "php": {
        "version": "7.4",
        "path": "/opt/remi/php74",
        "cli": "/opt/remi/php74/root/usr/bin/php"
      },
      "redis": {
        "host": "10.75.128.47",
        "port": 39861,
        "socket": "/var/run/redis-multi-a405fd09.redis/redis.sock",
        "version": "6"
      },
      "app": {
        "type": "wordpress",
        "version": "5.8",
        "admin": {
          "url": null,
          "username": "admin"
        },
        "updates": {
          "core": {
            "enabled": false,
            "minor_only": false,
            "updated_date": null,
            "disabled_date": 1629380926
          },
          "plugin": {
            "enabled": false,
            "minor_only": false,
            "updated_date": null,
            "disabled_date": 1629369997
          }
        },
        "upgrades": {
          "core": {
            "updated_date": 1629373042
          }
        }
      }
    },
    "options": {
      "nxcache_nocache": false,
      "nxcache_varnish": false,
      "nxcache_varnish_static": false,
      "nxcache_varnish_ttl": 120,
      "autoscale_enabled": true,
      "letsencrypt": {
        "enabled": true
      }
    },
    "access": {
      "url": "https://39869b24b8.1700.lwdns.dev/wp-admin/",
      "username": "admin"
    }
  },
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
  "project": {
    "id": 522,
    "identity": "39869b24b8.1700.lwdns.dev",
    "metadata": {
      "scope": "app-project",
      "uri": null
    }
  },
  "reference_account": null,
  "screenshot_url": "https://objects.liquidweb.services/mirador-stg/site/38114/virt-guest-cloudaccount-1091/36ab0548-110b-4b7e-ab15-521584409102.png",
  "service": {
    "id": 58378,
    "identity": "My WordPress Spark Plan 1",
    "metadata": {
      "scope": "service",
      "uri": "/v1/service/cloud-account/58378"
    },
    "status": "enabled",
    "state": "stable",
    "type": "virt-guest-cloud"
  },
  "ssl_cert": {
    "id": 627,
    "identity": "39869b24b8.1700.lwdns.dev",
    "metadata": {
      "scope": "ssl-cert",
      "uri": "/v1/ssl-certificate/627"
    }
  },
  "staging_account_count": 0,
  "state": "stable",
  "temp_domain": "39869b24b8.1700.lwdns.dev",
  "unix_username": "a405fd09"
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
