# Cloud Account

The cloud-account endpoint is use to both create and manage cloud accounts and many of the options of a cloud account and related service.

**End Point**

```
/cloud-account
```

**Accepted Verbs**
- GET
  - [Retrieve list of cloud accounts](#retrieve-list-of-cloud-accounts)
  - [Retrieve information on a specific cloud account and related service](#retrieve-information-on-a-specific-cloud-account-and-related-service)
  -[List All Backups](#list-all-backups)
- POST
  - [Creating a Cloud Account](#creating-a-cloud-account)
  - [Creating a Development Account](#creating-a-development-account)
  - [Clear Nginx Cache](#clear-nginx-cache)
  - [Create a Backup](#create-a-backup)
- DELETE
  - [Delete a Backup](#delete-a-backup)

## GET

### Retrieve list of cloud accounts
To retrieve a list of all the cloud accounts associated with an account make a call to `/cloud-account` with your API key.

__Example 1__
```shell
curl -v '__URL__/cloud-account' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'
```

This will return a very verbose JSON payload that will list the details of all of the cloud accounts associated with your account.

### Retrieve information on a specific cloud account and related service

To retrieve the details of a specific cloud account, you and append the `cloud_id`  to this endpoint. In the payload returned in the above command, cloud_id is found in each cloud account object in `cloud_account->account_id`.

__Example 2__
```shell
curl -v '__URL__/cloud-account/CLOUD_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'
```

This will return a similar payload to the first GET but it will be limited to a single cloud_account. This is how you check the state of a cloud account onces you have issued the POST described below. See [__Payload 2__](#payload3) for an example output of this command.

### List All Backups

The `cloud-account` endpoint can be used to list all the backups for a given cloud account whether they were created with the APU or the UI.

__Example 3__
```shell
curl -v '__URL__/cloud-account/CLOUD_ID/backup' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'
```

The payload returned is a list of all backups that have been created and not yet deleted.

__Payload 1__
```json
[
  {
    "filepath": "/home/a6fb203a/demo2.example.com/iworx-backup/demo2.example.com+full-single-Sep.18.2018-16.08.25.tgz",
    "filename": "demo2.example.com+full-single-Sep.18.2018-16.08.25.tgz",
    "filesize": "431.70 KB",
    "filesize_bytes": 442017,
    "type": "Full Backup",
    "domain_options": "single-domain",
    "filedate": 1537301308,
    "complete": true,
    "download_url": "https://69.160.55.105:2443/siteworx/index?action=sso&sid=85adbe280245e57fd549a846f21e243b&uri=L3NpdGV3b3J4L2Rvd25sb2FkP2FjdGlvbj1iYWNrdXAmZmlsZT1kZW1vMi5leGFtcGxlLmNvbSUyQmZ1bGwtc2luZ2xlLVNlcC4xOC4yMDE4LTE2LjA4LjI1LnRneiZkb21haW49ZGVtbzIuZXhhbXBsZS5jb20%3D"
  },
  {
    "filepath": "/home/a6fb203a/demo2.example.com/iworx-backup/demo2.example.com+full-single-Sep.18.2018-16.15.01.tgz",
    "filename": "demo2.example.com+full-single-Sep.18.2018-16.15.01.tgz",
    "filesize": "431.60 KB",
    "filesize_bytes": 442009,
    "type": "Full Backup",
    "domain_options": "single-domain",
    "filedate": 1537301704,
    "complete": true,
    "download_url": "https://69.160.55.105:2443/siteworx/index?action=sso&sid=7e1f3cf779227f86a0f3857d48cb8eab&uri=L3NpdGV3b3J4L2Rvd25sb2FkP2FjdGlvbj1iYWNrdXAmZmlsZT1kZW1vMi5leGFtcGxlLmNvbSUyQmZ1bGwtc2luZ2xlLVNlcC4xOC4yMDE4LTE2LjE1LjAxLnRneiZkb21haW49ZGVtbzIuZXhhbXBsZS5jb20%3D"
  }
]
```


## POST

### Creating a Cloud Account

Before we can issue a POST command, we need values for a few of the parameters. The required parameters for creating a cloud account are:

- The domain name that will be attached to this service
- The application we want to install
- The size of the server we want to install it on
- The cloud you want your account on
- Whether you want the system to auto-install the application for you.

Here is a sample payload

__Payload 2__
```json
{
  "domain": "example.com",
  "app_id": "33",
  "package_id": "710",
  "cloud_id": "1",
  "install_app": "on"
}
```

- `domain` is the domain name for the cloud account we will create. This is a required field and takes any valid (looking) domain name including sub-domains.
- `app_id` is the Nexcess id for the application you want to install See [Applications](Applications.md) to get a list of the available `app_id` values. This is a required filed and the value must be a valid application id.
- `package_id` is the Nexcess id for the server package you want to spin up. See 'Listing Packages' to get a list of available `package_id` values. This is a required field and the value must be a valid package id.
- `cloud_id` is the Nexcess id for the cloud (data center) you want to spin up your new account within.  See 'Listing Clouds' to get a list of available `cloud_id` values. This is a required field and the value must be a valid cloud id.
- `install_app` tells the system whether or not to actually install the application you requested or to only prepare the server environment for you to install the application later. This is an optional field. If it is not present, then "off" is assumed. If it is present and the value specified is "on" then the application will be installed.


__Example 4__
```shell
curl -v -X POST '__URL__/cloud-account' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
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

This will return to you a very large payload that will give you details about both the cloud account that is being created, and the service that it belongs to. It is important to note that the API queues the job to be done, it does not wait until the job is complete.

<a name="payload3">__Payload 3__</a>
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

Creating a cloud account is an out-of-bandwidth command. Receiving a 200 OK for a POST only means that the system has accepted your request. In the payload returned is the cloud account id that you can use as described above to check for the state of your cloud account.

There are 5 possible states your cloud can be in.

- **creating** This is the initial state. The cloud account will stay in this state until the initial creation of the clopud account has completed.
- **destroying** This is the state of a machine that has been required to be destroyed and approved. It is in htis state until the destroy process is complete. After this is complete the API will return 404 on all future calls to `/cloud-host/cloud_id`
- **failure** If for some reason the creating process did. not complete successfully, the cloud account will be assigned the state of failure.
- **installing** Once creating is complete, if you have requested that an application be installed, the cloud account will be put in the installing state. It will remain in this state until the application is successfully installed.
- **stable** The final state of the cloud account is stable. This is your signal that everything truly is 200 OK.


### Creating a Development Account

 Development accounts are a special type of account tied to a cloud account. As the name implies, they are for development purposes and not to be used for production. Development accounts are clones of production accounts. They are created in a very similar call for creating the production cloud account.

__Payload 4__
```json
{
  "domain": "development.demo2.example.com",
  "copy_account": "1",
  "scrub_account": "1",
  "package_id": "713",
  "ref_service_id": "58692",
  "ref_type": "development"
}
```

- `domain` is domain passed in has to be a subdomain of the production cloud account's domain. This is a required parameter.
- `package_id` This is the package to create and install the development environment within. This is a required parameter.
- `ref_service_id` This is the service_id associated with the parent cloud account. This is a required parameter.
- `ref_type` is the type of account being created. When creating a development account, specify **development**. This is a required parameter.
- `copy_account` is a boolean flag. If set to true then the environment of the production cloud account will be copied into the development environment. This is an optional parameter. If not present, false is assumed.
- `scrub_account` is a boolean flag. If set to true then data in the database will be anonymized. This is an optional parameter. If not present, false is assumed.

__Example 5__
```shell
curl -v -X POST '__URL__/extranet/cloud-account' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  --data-binary '{
    "domain": "development.demo2.example.com",
    "copy_account": true,
    "scrub_account": true,
    "package_id": "713",
    "ref_service_id" : "SERVICE_ID",
    "ref_type" : "development"
  }'
```

The payload returned from the command above is the same as [Payload 3](#payload3).


### Clear Nginx Cache

The `cloud-account` endpoint can be used to clear the Nginx cache on a given related service.

__Example 6__
```shell
curl -X POST '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
   -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
   -H 'Content-Type: application/json' \
   -H 'Accept: application/json' \
   --data-binary '{"_action": "purge-cache"}'
```

There is only one required parameter needed to clear the Nginx Cache.

- `_action` takes a single value of **purge-cache**.

The payload returned from the command above is the same as [Payload 3](#payload3).

The clearing of the cache is an out-of-bandwidth process. a 200 OK return indicates that the switch has been set but it can take a few minutes for the process to complete.

### Create a Backup

The `cloud-account` endpoint can be used to create an account backup.

__Example 7__
```shell
curl -X POST '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
   -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
   -H 'Content-Type: application/json' \
   -H 'Accept: application/json'
```

No parameters are available for this endpoint, however you do have to put the cloud account's ID in the URI.

__Payload 5__
```json
{
  "filepath": "/home/a6fb203a/demo2.example.com/iworx-backup/demo2.example.com+full-single-Sep.18.2018-16.15.01.tgz",
  "filename": "demo2.example.com+full-single-Sep.18.2018-16.15.01.tgz",
  "filesize": "431.60 KB",
  "filesize_bytes": 442009,
  "type": "Full Backup",
  "domain_options": "single-domain",
  "filedate": 1537301704,
  "complete": true
}
```

The payload returned in most cases describes the backup that will be created. Backups are an out-of-bandwidth process in almost all cases. In a very few cases, the backup will complete before the API returns. In these cases - very small sites or no files/DB ot be backed up - you will see that `complete` comes back as **true**.

In most cases, `complete` will come back as **false**. To check the status of your backup:

- Save off the file name
- Call [List All Backups](#list-all-backups)
- Iterate over the list of backups to find the one with your filename
- Check the status of `complete`

Once your backup is complete, you can use the URL provided in `download_url` to fetch the download.


# DELETE

## Delete a Backup

The `cloud-account` endpoint can be used to delete backups created either via the API or the UI.

__Example 8__
```shell
curl -X DELETE '__URL__/cloud-account/CLOUD_ACCOUNT_ID/backup/URL_ENCODED_BACKUP_FILENAME' \
   -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
   -H 'Content-Type: application/json' \
   -H 'Accept: application/json'
```

When you [List All Backups](#list-all-backups) each backup entry has a `file_name` property. This is a URL Encoded version of the file name and is safe to use as it is in the DELETE call. You need to append the file name to the backup URL and then call with the DELETE verb.

DELETing a backup will not return any payload. It will however return a 200 OK upon success.


# Wrap Up
This page has described the options available for the `/cloud-account` API endpoint. It has described the inputs as well as the outputs. It has described crating both a cloud account and a development environment.

