# Create a Cloud Account
The first thing we will do is create a cloud account. Before we can do this we need values for a few of the parameters. The required parameters for creating a cloud account are:

- The domain name that will be attached to this service
- The application we want to install
- The size of the server we want to install it on
- The datacenter you want your server in
- Whether you want the system to auto-install the application for you.

Here is a sample payload

```json
{
  "domain": "example.com",
  "app_id": "33",
  "package_id": "710",
  "cloud_id": "1",
  "install_app": "on"
}
```

- `domain` is the domain name for the cloud account we will create. This is a required field and takes any valid (looking) domain name including subdmains.
- `app_id` is the Nexcess id for the application you want to install See 'Listing Applications' to get a list of the available `app_id` values. This is a required filed and the value must be a valid application id.
- `package_id` is the Nexcess id for the server package you want to spin up. See 'Listing Packages' to get a list of available `package_id` values. This is a required field and the value must be a valid package id.
- `cloud_id` is the Nexcess id for the cloud (datacenter) you want to spin up your new account within.  See 'Listing Clouds' to get a list of available `cloud_id` values. This is a required field and the value must be a valid cloud id.
- `install_app` tells the system whether or not to actually install the application you requested or just prepare the server for it's install. This is an optional field. If it is not present, then "off" is assumed. If it is present and the value specified is "on" then the application will be installed.

> Note that this is an HTTP POST. (`-x POST`). If you  leave off the POST and instead issue a GET, the data will be ignored and the call will return a payload listing all existing Cloud Accounts for the account that owns the key. This is, of course, not the response we are interested in when trying to create a cloud account.

```shell
curl -v -X POST '__URL__/cloud-account' \
  -H 'Authorization: Bearer YOU_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  --data-binary '{
  "domain": "example.com",
  "app_id": "33",
  "package_id": "710",
  "cloud_id": "1",
  "install_app": "on"
}'
```

This will return to you a very large payload that will give you the details of **what is being created**. It is important to note that the API queues the job to be done, it does not wait until the job is complete.

```json
{
  "id": "SERVICE_ID",
  "identity": "example.com - nc.large",
  "is_real": true,
  "meta": {
    "scope": "service"
  },
  "type": "virt-guest-cloud",
  "status": "enabled",
  "description": "nc.large",
  "nickname": "",
  "next_bill_date": 1539489600,
  "main_ip": {
    "id": "xxx.xxx.xxx.xxx",
    "identity": "xxx.xxx.xxx.xxx",
    "is_real": true,
    "meta": {
      "scope": "ip-block"
    },
    "type": "ipv4",
    "status": "used",
    "real_id": 66348
  },
  "host": "cloudhost-45328.us-midwest-1.nxcli.net",
  "cloud_account": {
    "account_id": "CLOUD_ACCOUNT_ID",
    "host_id": 672,
    "domain": "example.com",
    "status": "used",
    "deploy_date": 1536951608,
    "deploy_complete_date": 0,
    "project_id": 897,
    "parent_account_id": 0,
    "reference_account_id": 0,
    "ssl_cert_id": 0,
    "state": "creating",
    "id": 1461,
    "identity": "example.com",
    "is_real": true,
    "meta": {
      "scope": "virt-guest-cloudaccount"
    },
    "ip": "xxx.xxx.xxx.xxx",
    "ipv4": "xxx.xxx.xxx.xxx",
    "is_dev_account": false,
    "temp_domain": "0e372454ad.nxcli.net",
    "cloudhost_hostname": "cloudhost-xxxxxx.cloud-name.nxcli.net",
    "unix_username": "xxxxxxxxx",
    "app": {
      "id": 33,
      "identity": "Wordpress 4",
      "is_real": true,
      "meta": {
        "scope": "app-app"
      },
      "type": "wordpress",
      "status": "active",
      "name": "Wordpress",
      "version": "4",
      "is_wordpress_based": true,
      "is_installable": true
    },
    "environment": {
      "software": {
        "php": {
          "version": "7.1",
          "path": "/opt/remi/php71",
          "cli": "/opt/remi/php71/root/usr/bin/php"
        },
        "redis": {
          "host": "",
          "port": "",
          "socket": "/var/run/redis-multi-a7af96a7.redis/redis.sock",
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
    "identity": "Chosen Cloud Description",
    "is_real": true,
    "meta": {
      "scope": "isolation-zone"
    }
  },
  "location": {
    "id": 1,
    "identity": "cloud-identifier",
    "is_real": true,
    "meta": {
      "scope": "virt-cloud"
    },
    "type": "openstack",
    "status": "active",
    "location": "Cloud Location",
    "location_code": "cloud-identifier",
    "country": "US"
  },
  "order": {
    "id": "xxxxx",
    "identity": "(xxxxx) Nexcess Client",
    "is_real": true,
    "meta": {
      "scope": "order"
    },
    "type": "virt-guest-cloud",
    "status": "allocated",
    "months": 1,
    "location": {
      "id": 1,
      "identity": "cloud-identifier",
      "is_real": true,
      "meta": {
        "scope": "virt-cloud"
      },
      "type": "openstack",
      "status": "active",
      "location": "Cloud Location",
      "location_code": "cloud-identifier",
      "country": "US"
    }
  },
  "dev_account_count": 0,
  "state": "creating",
  "child_cloud_accounts": []
}
```

# Checking the status of a Cloud Account
Once you have issued the Create Cloud Account command above, you can query the API periodically to check it's status. In the payload above you will notice a value `CLOUD_ACCOUNT_ID`. This will be an integer for the cloud account that you have just created. Use this id to check the status of your cloud account.

```shell
curl -v '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOU_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'
```

This will return you a JSON payload that resembles the one above. In this case we are looking for one important field in the payload, `STATE`.


```
  "state": "stable",
```

State can have one of five different states.

- creating
- destroying
- failure
- installing
- stable

While they are all self explanatory, in most cases, the one you are looking for is "stable". In the rare case that something went wrong in either creating your cloud account or installing the application requested, you will see the state of 'failure'. This is a fatal state that cannot be recovered from. If a cloud account fails, support will be in contact with you to discuss what went wrong.

Once your VM has reached the status of "stable", you are ready to begin working with it.

# Wrap Up
This page has described the commands necessary and the payloads returned when creating a Nexcess Cloud Account.