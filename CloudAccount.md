# Create a Cloud Account

**End Point**

```
/cloud-account
```

**Accepted Verbs**
- GET
- POST

## GET

To retrieve a list of the cloud accounts associated with an account make a call to `/cloud-account` with your API key.

```shell
curl -v '__URL__/cloud-account' \
  -H 'Authorization: Bearer YOU_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'
```
__Example 1__

This will return a very verbose JSON payload that describes each cloud account associated with your account.

To retrieve the details of a specific cloud account, you and append the `cloud_id`  to this endpoint. In the payload returned in the above command, cloud_id is found in each cloud account object in `cloud_account->account_id`.

```shell
curl -v '__URL__/cloud-account/CLOUD_ID' \
  -H 'Authorization: Bearer YOU_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'
```
__Example 2__

This will return a similar payload to the first GET but it will be limited to a single cloud_account. This is how you check the state of a cloud account onces you have issued the POST described below. See [__Payload 2__](#payload2) for an example output of this command.

## POST

Before we can issue a POST command, we need values for a few of the parameters. The required parameters for creating a cloud account are:

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
__Payload 1__


- `domain` is the domain name for the cloud account we will create. This is a required field and takes any valid (looking) domain name including sub-domains.
- `app_id` is the Nexcess id for the application you want to install See 'Listing Applications' to get a list of the available `app_id` values. This is a required filed and the value must be a valid application id.
- `package_id` is the Nexcess id for the server package you want to spin up. See 'Listing Packages' to get a list of available `package_id` values. This is a required field and the value must be a valid package id.
- `cloud_id` is the Nexcess id for the cloud (data center) you want to spin up your new account within.  See 'Listing Clouds' to get a list of available `cloud_id` values. This is a required field and the value must be a valid cloud id.
- `install_app` tells the system whether or not to actually install the application you requested or just prepare the server for it's install. This is an optional field. If it is not present, then "off" is assumed. If it is present and the value specified is "on" then the application will be installed.


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
__Example 3__

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
[__Payload 2__](payload2)

Creating a cloud account is an out-of-bandwidth command. Receiving a 200 OK for a POST only mens that the system has accepted your request. In the payload returned is the cloud account id that you can use as described above to check for the state of your cloud account.

There are 5 possible states your cloud can be in.

- **creating** This is the initial state. The cloud account will stay in this state until the initial creation of the clopud account has completed.
- **destroying** This is the state of a machine that has been required to be destroyed and approved. It is in htis state until the destroy process is complete. After this is complete the API will return 404 on all future calls to `/cloud-host/cloud_id`
- **failure** If for some reason the creating process did. not complete successfully, the cloud account will be assigned the state of failure.
- **installing** Once creating is complete, if you have requested that an application be installed, the cloud account will be put in the installing state. It will remain in this state until the application is successfully installed.
- **stable** The final state of the cloud account is stable. This is your signal that everything truly is 200 OK.



# Wrap Up
This page has described the commands available for the cloud-account API endpoint.
