# Service

**End Point**

```
/service
```
The `/service` endpoint allows you to query and modify some of the attributes of a given service. When you create a cloud-account, a service is also created and associated with that cloud account. The service represents the actual server and application installed and contains all the technical parameters that can be see or modified.

**Accepted Verbs**

- GET
  - [Get the status of a service](#get-the-staus-of-a-service)
- POST

## GET

### Get the status of a service

Querying the `/service` endpoint with a service_id will return you the complete list of attributes for that service.
```shell
__Example 1__
curl -v '__URL__/service/SERVICE_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'
```

This returns a very verbose payload that details everything known about a service.

<a name="payload1">__Payload 1__</a>
```json
{
  "service_id": 58692,
  "client_id": 0000000,
  "package_id": 716,
  "parent_id": 0,
  "discount_id": 0,
  "last_bill_date": 1537181230,
  "next_bill_date": 1539748800,
  "term": 1,
  "pricing_type": "monthly",
  "status": "enabled",
  "state": "stable",
  "override_price": 10,
  "override_percent": 0,
  "override_addons": "no",
  "override_bandwidth": 0,
  "bandwidth_overage_fee": 0,
  "bandwidth_profile_id": 2,
  "start_date": 1537181231,
  "type": "virt-guest-cloud",
  "auto_renew": "yes",
  "description": "nc.small-test",
  "cloud_id": 1,
  "nickname": "",
  "id": 58692,
  "identity": "nc.small-test",
  "is_real": true,
  "meta": {
    "scope": "service"
  },
  "host": "example.com",
  "cloud_account": {
    "account_id": 00000,
    "host_id": 00000,
    "domain": "example.com",
    "status": "used",
    "deploy_date": 1537181239,
    "deploy_complete_date": 1537181272,
    "project_id": 898,
    "parent_account_id": 0,
    "reference_account_id": 0,
    "ssl_cert_id": 0,
    "state": "stable",
    "id": 1462,
    "identity": "dexample.com",
    "is_real": true,
    "meta": {
      "scope": "virt-guest-cloudaccount"
    },
    "ip": "xxx.xxx.xxx.xxx",
    "ipv4": "xxx.xxx.xxx.xxx",
    "is_dev_account": false,
    "temp_domain": "be8bac43eb.example.com",
    "cloudhost_hostname": "cloudhost-96857.us-southeast-1.example.com",
    "unix_username": "XXXXXXX",
    "app": {
      "id": 28,
      "identity": "Magento 2",
      "is_real": true,
      "meta": {
        "scope": "app-app"
      },
      "type": "magento",
      "status": "active",
      "name": "Magento",
      "version": "2",
      "is_wordpress_based": false,
      "is_installable": true
    },
    "environment": {
      "software": {
        "php": {
          "version": "7.2",
          "path": "/opt/remi/php72",
          "cli": "/opt/remi/php72/root/usr/bin/php"
        },
        "redis": {
          "host": "",
          "port": "",
          "socket": "/var/run/redis-multi-a6fb203a.redis/redis.sock",
          "version": "3.2"
        }
      },
      "options": {
        "nxcache_nocache": false,
        "nxcache_varnish": false,
        "nxcache_varnish_static": false,
        "nxcache_varnish_ttl": 120,
        "autoscale_enabled": true
      },
      "access": []
    }
  },
  "environment_type": "production",
  "isolation_zone": {
    "id": 1,
    "identity": "Southfield, MI",
    "is_real": true,
    "meta": {
      "scope": "isolation-zone"
    }
  },
  "location": {
    "id": 1,
    "identity": "us-southeast-1",
    "is_real": true,
    "meta": {
      "scope": "virt-cloud"
    },
    "type": "openstack",
    "status": "active",
    "location": "Southfield, MI",
    "location_code": "us-southeast-1",
    "country": "US"
  },
  "order": {
    "id": 00000,
    "identity": "(00000) Nexcess Client",
    "is_real": true,
    "meta": {
      "scope": "order"
    },
    "type": "virt-guest-cloud",
    "status": "completed",
    "months": 1,
    "location": {
      "id": 1,
      "identity": "us-southeast-1",
      "is_real": true,
      "meta": {
        "scope": "virt-cloud"
      },
      "type": "openstack",
      "status": "active",
      "location": "Southfield, MI",
      "location_code": "us-southeast-1",
      "country": "US"
    }
  },
  "dev_account_count": 0,
  "child_cloud_accounts": [
    {
      "id": 1463,
      "identity": "dexample.com",
      "is_real": true,
      "meta": {
        "scope": "virt-guest-cloudaccount"
      },
      "status": "used",
      "ip": "",
      "ipv4": "xxx.xxx.xxx.xxx",
      "domain": "demo2a.example.com",
      "is_dev_account": false,
      "temp_domain": "8181efcfc0-1463.example.com",
      "cloudhost_hostname": "cloudhost-96857.us-southeast-1.example.com",
      "unix_username": "a6fb203a",
      "app": {
        "id": 30,
        "identity": "Flexible ",
        "is_real": true,
        "meta": {
          "scope": "app-app"
        },
        "type": "generic",
        "status": "active",
        "name": "Flexible",
        "version": "",
        "is_wordpress_based": false,
        "is_installable": false
      },
      "state": "stable",
      "parent": {
        "id": 0000,
        "identity": "demo2.example.com",
        "is_real": true,
        "meta": {
          "scope": "virt-guest-cloudaccount"
        },
        "status": "used",
        "ip": "xxx.xxx.xxx.xxx",
        "ipv4": "xxx.xxx.xxx.xxx",
        "domain": "demo2.example.com",
        "is_dev_account": false,
        "temp_domain": "be8bac43eb.example.com",
        "cloudhost_hostname": "cloudhost-96857.us-southeast-1.example.com",
        "unix_username": "a6fb203a",
        "app": {
          "id": 28,
          "identity": "Magento 2",
          "is_real": true,
          "meta": {
            "scope": "app-app"
          },
          "type": "magento",
          "status": "active",
          "name": "Magento",
          "version": "2",
          "is_wordpress_based": false,
          "is_installable": true
        },
        "state": "stable"
      },
      "deploy_complete_date": 1537181776
    }
  ],
  "package": {
    "id": 716,
    "identity": "nc.small-test",
    "is_real": true,
    "meta": {
      "scope": "package"
    },
    "type": "virt-guest-cloud",
    "status": "web-active",
    "virt_dedicated_guest": 0
  },
  "bill_day": "17",
  "billing_term": {
    "type": "monthly",
    "months": 1,
    "years": 0,
    "description": "Monthly",
    "amount": 10
  },
  "is_managed": false,
  "balance": 0,
  "is_overdue": false,
  "addons": [],
  "has_invoices": true,
  "has_paypal_subscription": false,
  "paypal_subscribe_link": "",
  "is_cancellable": true,
  "settings": {
    "extranet.disable-networking.enabled": false
  },
  "is_rebootable": false,
  "has_stored_password": false,
  "can_change_root_password": false,
  "can_change_hostname": true,
  "ips": [
    {
      "id": "xxx.xxx.xxx.xxx",
      "identity": "xxx.xxx.xxx.xxx",
      "is_real": true,
      "meta": {
        "scope": "ip-block"
      },
      "type": "ipv4",
      "status": "used",
      "real_id": 68866
    },
    {
      "id": "xxx.xxx.xxx.xxx",
      "identity": "xxx.xxx.xxx.xxx",
      "is_real": true,
      "meta": {
        "scope": "ip-block"
      },
      "type": "ipv4",
      "status": "used",
      "real_id": 66340
    },
    {
      "id": "xxx.xxx.xxx.xxx",
      "identity": "xxx.xxx.xxx.xxx",
      "is_real": true,
      "meta": {
        "scope": "ip-block"
      },
      "type": "ipv4",
      "status": "unused",
      "real_id": 68872
    },
    {
      "id": "xxx.xxx.xxx.xxx",
      "identity": "xxx.xxx.xxx.xxx",
      "is_real": true,
      "meta": {
        "scope": "ip-block"
      },
      "type": "ipv4",
      "status": "unused",
      "real_id": 4742
    }
  ],
  "has_console": false,
  "bandwidth": {
    "used": {
      "total": 0,
      "billable": 0
    },
    "projected": {
      "total": 0,
      "billable": 0
    },
    "previous": {
      "total": 0,
      "billable": 0
    },
    "given": "100",
    "type": "GB"
  }
}
```


## POST

Most of the properties of a service  cannot currently be changed via the API. However, one thing can currently be changed, the version of PHP this service uses.
 
__Example 2__
```shell
curl -v '__URL__/service/SERVICE_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json' \
  --data-binary '{"_action": "set-php-version", "php_version": "7.2"}'
```

__Parameters__

| Name | Description | Required |
| :--- | :--- | :---: |
| `set-php-version` | Can either be "7.1 or 7.2" | YES |

This end point may take some time to return. Once it does, it will return the complete service object as seen on [Payload 1](#payload1). Examining the `environment->software->php->version` property will show you the newly changed version.

# Wrapup
The `/service` endpoint allows us to query the properties of a given service and change those properties that have been exposed for change.