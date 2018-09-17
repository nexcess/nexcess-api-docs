# List Applications

**End Point**
```
/app
```

**Accepted Verbs**
- GET

## GET

This endpoint lists the applications that can be installed on cloud accounts. There are no required parameters to make a call to this endpoint.

__Example 1__
```shell
curl -v '__URL__/app' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'

```

__Payload 1__
```json
[
  {
    "app_id": 28,
    "name": "Magento",
    "version": "2",
    "type": "magento",
    "ansible_repo": "",
    "ansible_branch": "master",
    "ansible_role_alias": "",
    "git_repo": "",
    "git_branch": "master",
    "configuration_template_json": "",
    "status": "active",
    "id": 28,
    "identity": "Magento 2",
    "is_real": true,
    "meta": {
      "scope": "app-app"
    },
    "is_wordpress_based": false,
    "is_installable": true
  }
]
```

The above payload is one of the entries returned.  The `app_id` is the number you will use when making calls to [cloud-account](CloudAccount.md).

> In [cloud-account](CloudAccount.md) you have the option to specify the option `install_app`. This option is only relevant for Applications where `is_installable` is set to true. If `is_installable` is set to false, `install_app` will be silently ignored.

