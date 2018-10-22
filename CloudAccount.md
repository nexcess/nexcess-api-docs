# Cloud Account

The cloud-account endpoint is use to both create and manage cloud accounts and many of the options of a cloud account and related service.

**End Point**

```
/cloud-account
```

**Accepted Verbs**
- GET
  - [Retrieve a list of cloud accounts](#retrieve-list-of-cloud-accounts)
  - [Retrieve information on a specific cloud account](#retrieve-information-on-a-specific-cloud-account-and-related-service)
  - [List all backups](#list-all-backups)
  - [Download a backup](#download-a-backup)
  - [Get available versions of PHP](#get-the-list-of-php-versions)
  - [Get remote user name](#get-remote-user-name)
  - [Get usage metrics](#get-usage-metrics)
  - [List pointer domains](#list-pointer-domains)

- POST
  - [Create a cloud account](#create-a-cloud-account)
  - [Creating a development account](#creating-a-development-account)
  - [Clear Nginx cache](#clear-nginx-cache)
  - [Create a backup](#create-a-backup)
  - [Change PHP version](#change-php-version)
  - [Resize a cloud account](#resize)
  - [Toggle autoscale](#toggle-autoscale)
  - [Toggle Varnish Caching](#toggle-varnish-caching)
  - [Create remote user password](#create-remote-user-password)
  - [Add pointer domain](#add-pointer-domain)
  - [Remove pointer domain](#remove-pointer-domain)
  - [Attach SSL Certificate](#attach-ssl-certificate)
- DELETE
  - [Delete a backup](#delete-a-backup)

## GET

### Retrieve list of cloud accounts
To retrieve a list of all the cloud accounts associated with an account make a call to `/cloud-account` with an API key.

__Example 1__
```shell
curl '__URL__/cloud-account' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'
```

This will return a JSON payload that will list the details of all of the cloud accounts associated with the the account.

### Retrieve information on a specific cloud account and related service

This endpoint allows for the retrieval of the details about a specified cloud account. The value passed in for `CLOUD_ACCOUNT_ID` should match one of the `account_id` values returned from [Retrieve a list of cloud accounts](#retrieve-list-of-cloud-accounts).


__Example 2__
```shell
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'
```

This will return a similar payload to [Payload 7](#payload7).

### List all backups

The `cloud-account` endpoint can be used to list all the backups for a given cloud account whether they were created with the APU or the UI.

__Example 3__
```shell
curl '__URL__/cloud-account/CLOUD_ID/backup' \
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

### Download a backup

Downloading a backup using the API and curl requires a few extra switches. When a backup is complete (`complete` === `true`), `download_url` will be added to the payload returned from [List all backups](#list-all-backups). That URL is the URL used to download the backup file. That URL however, will redirect at least once. Additionally, it will set cookies to let the redirected URL know that authorization has been completed. Therefore, when using curl from the command line:

- `-L` must be specified so that curl will follow redirects
- `-k` must be specified so that curl will not reject the certificate
- `-b` must be specified so that curls "cookie engine" will be engaged and cookies will be stored and passed

It is also a good idea to specific the `-o LOCAL FILE NAME` option to store the contents of the file locally unless the contents are being piped to another command for additional processing.

> When using wget, no additional parameters are needed other than the URL.

__Example 4__
```shell
curl -L -k -b  -o LOCAL_FILE_NAME 'DOWNLOAD_URL' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'
```

The only payload returned is the binary contents of the file requested.


### Get the List of PHP Versions

In the POST section there is an endpoint that will allow for the changing of the version of PHP installed on a given cloud account. Not all versions of PHP are supported. In most cases, the last four or five minor versions are available. The actual version installed will be the latest patch level released for the version chosen. (e.g. if 7.1 is chosen then 7.1.22 will be installed.)

__Example 5__
```shell
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID/get-php-versions' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json'
```

The payload returned is an array of version numbers to choose from. These are the only versions available for install.

__Payload 2__
```json
[
  "5.6",
  "7.0",
  "7.1",
  "7.2"
]
```

### Get remote user name

Each cloud account is assigned 'remote user name'. This is the user for ssh and sftp. This endpoint allows for the retrieval of that user name.

__Example 6__
```shell
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID/get-remote-username' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json'
```

There are two possible payloads that can be returned from this endpoint. The difference between the two is whether or not the cloud account has an un-viewed password for the remote user. All passwords are stored as encrypted 'datashares'. In the case of the password for the remote user, it can only be viewed once. Once viewed, it is deleted. If the password for the remote user has already been viewed the this is the payload that will be returned.

__Payload 3__
```json
{
  "username": "xxxxxxxxxx"
}
```

If the remote user has an un-viewed password then the details of the password datashare - not including the password itself - are appended to the payload.

__Payload 4__
```json
{
  "username": "xxxxxxxxxx",
  "password_share": {
    "id": 2238,
    "identity": "",
    "is_real": true,
    "meta": {
      "scope": "datashare"
    },
    "type": "ssh-password",
    "uuid": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx",
    "share_date": xxxxxxxxxxx,
    "expiration_date": xxxxxxxxxx,
    "uses": 0,
    "max_uses": 1,
    "owner": "virt-guest-cloudaccount",
    "owner_id": CLOUD_ACCOUNT_ID,
    "owner_object": {
      "id": CLOUD_ACCOUNT_ID,
      "identity": "demo.example.com",
      "is_real": true,
      "meta": {
        "scope": "virt-guest-cloudaccount"
      },
      "status": "used",
      "ip": "xxx.xxx.xxx.xxx",
      "ipv4": "xxx.xxx.xxx.xxx",
      "domain": "demo.example.com",
      "is_dev_account": false,
      "temp_domain": "xxxxxxxx-xxxx-xxxx-xxxx-xxxxxxxxxxxx.nxcli.net",
      "cloudhost_hostname": "xxxxxxxxxxxxxxx.us-midwest-1.nxcli.net",
      "unix_username": "a6f9c6b6",
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
      "state": "stable"
    },
    "expired": false,
    "link_to": "user",
    "link_to_id": 61417,
    "link_to_object": {
      "id": 61417,
      "identity": "sample@example.com",
      "is_real": true,
      "meta": {
        "scope": "user"
      },
      "prominent": false
    }
  }
}
```

If the password has already been viewed but was not recorded, it cannot be retrieved. However, a new password can be generated by using [Create remote user password](#create-remote-user-password).

### Get usage metrics

This endpoint is used to retrieve the storage and bandwidth metrics associated with a given cloud account.

__Example 7__
```shell
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID/get-usage-metrics' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json'
```

The payload that returns from this call will look like this.

__Payload 5__
```json
{
  "storage_gb": 5,
  "storage_used_gb": 0.05,
  "storage_used_pct": 0.07,
  "bandwidth_gb": 100,
  "bandwidth_used_gb": 0,
  "bandwidth_used_pct": 0
}
```

### List pointer domains

This endpoint can be used to retrieve the storage and bandwidth metrics associated with a given cloud account.

__Example 8__
```shell
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID/get-pointer-domains' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json'
```

The payload returned contains all of the pointer domains for the given cloud account. After the pointer domains is a list of the types of pointer domains that can be set. These types play a role when [adding a pointer domain](#add-pointer-domain).

__Payload 6__
```json
{
  "pointers": [
    {
      "domain": "bob.example.com",
      "points_to": "1538072470.example.com",
      "type": "LG_SERVER_ALIAS",
      "mail_alias": "Yes"
    },
    {
      "domain": "alice.example.com",
      "points_to": "http://1538072470.example.com",
      "type": "redirect (302)",
      "mail_alias": "Yes"
    },
    {
      "domain": "ted.example.com",
      "points_to": "http://1538072470.example.com",
      "type": "redirect (301)",
      "mail_alias": "Yes"
    }
  ],
  "types": {
    "redir_type_301": "redirect_301",
    "redir_type_302": "redirect_302",
    "redir_type_alias": "server_alias"
  }
}
```



## POST

### Create a Cloud Account

Before creating a cloud account, the values of several of the parameters will have to be fetched. The required parameters for creating a cloud account are:

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
|`domain`| The domain name for the cloud account we will create. This is a required field and takes any valid (looking) domain name including sub-domains.| String | YES |
|`app_id`|the system id for the application to be install See [Applications](Applications.md) to get a list of the available `app_id` values. | Integer | YES |
| `package_id` | the system id for the server package to be spun up. See '[Listing Packages](Packages.md)' to get a list of available `package_id` values. | Integer | YES |
| `cloud_id` | The system id for the cloud (data center) to spin up the new account in.  See '[Listing Clouds](Clouds.md)' to get a list of available `cloud_id` values. | Integer | YES |
| `install_app` | "ON" or "OFF" (TRUE or FALSE).<br >Tells the system whether or not to actually install the application requested or to only prepare the server environment.  | Boolean | NO |


__Example 9__
```shell
curl '__URL__/cloud-account' \
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

This will return a payload that will give details about both the cloud account that is being created, and the service that it belongs to. It is important to note that the API queues the job to be done, it does not wait until the job is complete. Use the value returned in in the `account_id` [Retrieve information on a specific cloud account](#retrieve-information-on-a-specific-cloud-account-and-related-service) endpoint to poll for updates. As soon as `state` returns as **stable**, the cloud account is ready to use.


<a name="payload7">__Payload 7__</a>
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
    "temp_domain": "xxxxxxxxx.nxcli.net",
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

Creating a cloud account is an out-of-bandwidth command. Receiving a 200 OK for a POST only means that the system has accepted the request. In the payload returned is the cloud account id that can be used as described above to check for the state of the cloud account.

There are 5 possible states a cloud account can be in.

| State | Description |
| :--- | :--- |
| **creating** | The initial state. The cloud account will stay in this state until the initial creation of the cloud account has completed. |
| **destroying** | The state of a machine that has been required to be destroyed and approved. It is in this state until the destroy process is complete. After this is complete the API will return 404 on all future calls to `/cloud-host/cloud_id` |
| **failure** | If for some reason the creating process did not complete successfully, the cloud account will be assigned the state of failure. |
| **installing** | Once creating is complete, if `install_app` was set to `on`, the application be installed. The cloud account will be put in the **installing** state. It will remain in this state until the application is successfully installed. |
| **stable** | The final state of the cloud account is stable. This is the signal that everything truly is 200 OK. |


### Creating a development account

 Development accounts are a special type of account tied to a cloud account. As the name implies, they are for development purposes and not to be used for production. Development accounts are clones of production accounts. They are created in a very similar call for creating the production cloud account.


__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
| `domain` | Has to be a sub-domain of the production cloud account's domain. | String | YES |
| `package_id` | The service_id associated with the parent cloud account. | Integer | YES |
| `ref_type` | `development` | String | YES |
| `copy_account` | If set to true then the environment of the production cloud account will be copied into the development environment. | Boolean | NO |
| `scrub_account` | `purge-cache` | Boolean | YES |
| `_action` | If set to true then data in the database will be anonymized. This is an optional parameter. | Boolean | NO |

__Example 10__
```shell
curl '__URL__/cloud-account' \
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

The payload returned from the command above is the same as [Payload 7](#payload7).


### Clear Nginx cache

The `cloud-account` endpoint can be used to clear the Nginx cache on a given related service.

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
| `_action` | `purge-cache` | String | YES |

__Example 11__
```shell
curl -X POST '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  --data-binary '{"_action": "purge-cache"}'
```

The payload returned from the command above is the same as [Payload 7](#payload7).

The clearing of the cache is an out-of-bandwidth process. A 200 OK return indicates that the switch has been set but it can take a few minutes for the process to complete.

### Create a backup

The `cloud-account` endpoint can be used to create an account backup.

__Example 12__
```shell
curl -X POST '__URL__/cloud-account/CLOUD_ACCOUNT_ID/backup
' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'
```

No parameters are available for this endpoint.

__Payload 8__
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

The payload returned in most cases describes the backup that will be created. Backups are an out-of-bandwidth process in almost all cases. In a very few cases, the backup will complete before the API returns. In these cases - very small sites or no files/DB to be backed up - `complete` will be returned as **true**.

In most cases, `complete` will come back as **false**. To check the status of a backup:

- Copy the file name
- Call [List All Backups](#list-all-backups)
- Iterate over the list of backups to find the one with the filename captured above
- Check the status of `complete`

Once the backup is complete, the URL provided in `download_url` can be used to fetch the backup file.


### Change PHP version

This endpoint is used to change the version of PHP installed in the specified cloud account.
The end point [get-php-versions](#get-the-list-of-php-versions) is used to retrieve a list of the valid versions of PHP that can be installed on a cloud account. This endpoint allows for the actual switching of the versions.

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
| `_action` | `set-php-version` | String | YES |
| `php_version` | One of the valid PHP versions listed by the [Get available versions of PHP](#get-the-list-of-php-versions) endpoint. | String | YES |


__Example 13__
```shell
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  --data-binary '{"_action": "set-php-version", "php_version": "PHP_VERSION"}'
```


The payload that returns is identical to [Payload 7](#payload7). The difference will be that in the environment section, the requested version of PHP will be listed.

__Payload 9__
```
"environment": {
  "software": {
    "php": {
      "version": "7.2",
      "path": "/opt/remi/php72",
      "cli": "/opt/remi/php72/root/usr/bin/php"
    },

```

### Resize

A cloud account can be resized both up and down. If the cloud account is a shared account, the resizing will take place in the background and a switch will be made once its state is "stable". This results in almost zero downtime. If the cloud account is a dedicated account then it will be taken off-line and resized.

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
| `_action` | `resize` | String | YES |
| `package_id` | the Nexcess id for the new server package to size the cloud account to. See '[Listing Packages](Packages.md)' to get a list of available `package_id` values. | Integer | YES |


__Example 14__
```shell
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  --data-binary '{"_action": "resize", "package_id": "NEW_PACKAGE_ID"}'
```

The payload that returns is identical to [Payload 7](#payload7). The difference will be that the package_id will reflect the new package.


### Toggle autoscale

Autoscale is a feature whereby a cloud account can be automatically moved up to the next package size if it exceeds it's max allocated concurrent users. This prevents a maxed out cloud account from dropping users during peak times. If off, when a cloud account exceeds it's max allocated concurrent users, additional users will be disconnected until others drop off. Autoscale can be turned on or off via this endpoint.

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
| `_action` | `set-autoscale` | String |YES |
| `autoscale` | `true` or `false` | Boolean | YES |


__Example 15__
```shell
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  --data-binary '{"_action": "set-autoscale", "autoscale": false}'
```

The payload that returns is identical to [Payload 7](#payload7). The difference will be that in the options section of the payload, `autoscale_enabled` will reflect the change requested.

__Payload 10__
```
"options": {
  "nxcache_nocache": false,
  "nxcache_varnish": false,
  "nxcache_varnish_static": false,
  "nxcache_varnish_ttl": 120,
  "autoscale_enabled": false
},
```

### Toggle Varnish caching

All cloud accounts come with [Varnish](https://varnish-cache.org) installed. By default, Varnish caching is disabled. This endpoint allows for Varnish to be toggled on and off.

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
| `_action` | `set-varnish` | String | YES |
| `enabled` | `true` or `false` | Boolean | YES |


__Example 16__
```shell
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  --data-binary '{"_action": "set-varnish","enabled": true}'

```

The payload that returns is identical to [Payload 7](#payload7). The difference will be that in the options section of the payload, `nxcache_varnish` will reflect the change requested.

__Payload 11__
```
"options": {
  "nxcache_nocache": false,
  "nxcache_varnish": false,
  "nxcache_varnish_static": false,
  "nxcache_varnish_ttl": 120,
  "autoscale_enabled": false
},
```


### Create remote user password

Cloud accounts can be accessed by users using either sftp or ssh. The endpoint [Get remote user name](#get-remote-user-name) can be used to retrieve the user name assigned to the account for this purpose. Passwords are stored in encrypted datashares. They can only be accessed a single time. If a password has been forgotten then the only recourse is to generate a new password datashare. This endpoint will accomplish that. The password itself however, cannot be viewed via the API. Users will have to log into their account to retrieve the new password.

**WARNING**: Calling this endpoint and creating a new password will  immediately invalidate the previous password.

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
| `_action` | `set-set-remote-password` | String | YES |


__Example 17__
```shell
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  --data-binary '{"_action": "set-remote-password"}'

```

The payload that returns is identical to the payload returned for [Get remote user name](#get-remote-user-name) when a password share is set.

__Payload 12__
```
"options": {
  "nxcache_nocache": false,
  "nxcache_varnish": false,
  "nxcache_varnish_static": false,
  "nxcache_varnish_ttl": 120,
  "autoscale_enabled": false
},
```

### Add pointer domain

This endpoint is used to add "Server Aliases", "301 Redirects" and "302 Redirects" to a cloud account.

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
| `_action` | `pointer-domain` | String | YES |
| `type` | One of three possible values: <br>- redir_type_301<br>- redir_type_302<br>- redir_type_alias |  String | YES |
| `domain` | Any valid domain name  | String | YES |


__Example 18__
```shell
# Add Pointer Domain
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  --data-binary '{"_action": "add-pointer-domain","type": "redir_type_alias","domain":"pointerdomain.example.com"}'
```

The payload that returned is the name of the domain pointer added.

__Payload 13__
```
{
  "domain": "pointerdomain.example.com"
}
```

### Remove pointer domain

This endpoint is used to remove pointer domain names from a cloud account.

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
| `_action` | `remove-pointer-domain` | String | YES |
| `domain` | The domain to be removed  | String | YES |

__Example 19__
```shell
# Add Pointer Domain
curl '__URL__/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  --data-binary '{"_action": "remove-pointer-domain", "domain":"pointerdomain.example.com"}'
```

The payload that returned is the name of the domain pointer removed.

__Payload 4__
```
{
  "domain": "pointerdomain.example.com"
}
```

If a domain is specified that does not exist as a pointer on the given cloud account a **422 Invalid Domain** will be returned.

### Attach SSL Certificate

This endpoint can be used in two ways.

1. Attach an SSL certificate that was imported into the system using [Import Certificate](Ssl-cert.md/#import-certificate) to the specified cloud account.
1. Add a new certificate/key combo into the system and attach the resulting ssl-cert to the specified cloud account.

#### Method #1

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
| `_action` | `install-ssl` | String | YES |
| `cert_id` | The `cert_id` returned when the certificate was added to the system. | Integer | YES |

__Example 20__
```shell
# Add Pointer Domain
curl '__URL__/extranet/cloud-account/CLOUD_ACCOUNT_ID' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json' \
  --data-binary '{"_action": "install-ssl", "cert_id": XXX}'
```

Upon success, this endpoint will return a 200 OK. The payload returned is identical to [Payload 7](#payload7). The difference is that `ssl_cert_id` will be populated with the passed in `cert_id`.

#### Method #2
__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
| `_action` | `install-ssl` | String | YES |
|`crt`| The certificate | String | YES |
|`key`| The private key | String | YES |
|`chain_cert`| Additional chain certificate | String | NO |

This method is functionally identical to [Import Certificate](Ssl-cert.md/#import-certificate) with the added action that it will also attach the certificate to the cloud account.

__Example 21__
```shell
#!/bin/bash
CHAIN="-----BEGIN CERTIFICATE-----
MIIGCDCCA/CgAwIBAgIQKy5u6tl1NmwUim7bo3yMBzANBgkqhkiG9w0BAQwFADCB
         ...Many more lines that look like that...
lBlGGSW4gNfL1IYoakRwJiNiqZ+Gb7+6kHDSVneFeO/qJakXzlByjAA6quPbYzSf
+AZxAeKCINT+b72x
-----END CERTIFICATE-----"

CRT="-----BEGIN CERTIFICATE-----
MIIGbDCCBVSgAwIBAgIQfpsSGBm0aOWQUqAGPoxrizANBgkqhkiG9w0BAQsFADCB
         ...Many more lines that look like that...
gInCCoyPSIRMKy1l84XmzgFV065g3kqxHCK8O0jpkFWgF2xbZBJCj0tWnNaWXPId
df6VNFF4+x1ub1x92UZ6ag==
-----END CERTIFICATE-----"

KEY="-----BEGIN PRIVATE KEY-----
MIIJQwIBADANBgkqhkiG9w0BAQEFAASCCS0wggkpAgEAAoICAQCliHpsXji5TOQZ
        ...Many MANY more lines that look like that...
mWvRtmCdwO45XMKPLkglubG/PS/GEgXOscvT0mjExPAE+zHmnEShgN3Ph8ex2O2U
WS4xRl9VsWExMgBcPlqbUS/Uez+XTAw=
-----END PRIVATE KEY-----"

KEY=$(echo "$KEY" | php -r 'echo json_encode(file_get_contents("php://stdin"));' )
CRT=$(echo "$CRT" | php -r 'echo json_encode(file_get_contents("php://stdin"));' )
CHAIN=$(echo "$CHAIN" | php -r 'echo json_encode(file_get_contents("php://stdin"));' )

curl -v '__URL__/extranet/cloud-account/CLOUD_ACCOUT_ID' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json' \
     --data-binary '{"_action":"install-ssl", chain_cert": '"$CHAIN"', "crt": '"$CRT"', "key": '"$KEY"'}'
```
Upon success, this endpoint will return a 200 OK. The payload returned is identical to [Payload 7](#payload7). The difference is that `ssl_cert_id` will be populated with the passed in `cert_id`.

# DELETE

## Delete a Backup

The `cloud-account` endpoint can be used to delete backups created either via the API or the UI. Use the DELETE verb and on the url pass in the `cloud_id` along with the url encoded name of the backup file.

__Example 22__
```shell
curl -X DELETE '__URL__/cloud-account/CLOUD_ACCOUNT_ID/backup/URL_ENCODED_BACKUP_FILENAME' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Content-Type: application/json' \
  -H 'Accept: application/json'
```

Each entity returned in the [List All Backups](#list-all-backups) payload has a `file_name` property. This is a URL Encoded version of the file name and is safe to use as it is in the DELETE call.

DELETing a backup will not return any payload. It will however return a 200 OK upon success.



