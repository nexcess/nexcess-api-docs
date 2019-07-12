# List Packages

***Endpoint***
```
/package?type=virt-guest-cloud&environment_type=production
```

**Accepted Verbs**
- GET
  - [Applications that can be installed](#applications-that-can-be-installed)
  - [Types of Certificates that can be purchased](#types-of-certificates-that-can-be-purchased)

## GET

### Applications that can be installed
This endpoint lists the applications that can be installed on cloud accounts.

__Parameters__

| Name | Value | Type | Required |
| :--- | :--- | :---: | :---: |
| `type` | `virt-guest-cloud` | String | YES |
| `environment_type` | `production` NOTE: There are two different environment types supported by the API, **production** and **development**. Use **production** for a list of the packages that can be use when creating any normal cloud account. Use **development** for a list of the packages that can be used when creating development accounts. | String | YES |


__Example 1__
```shell
curl -v '__URL__/package?type=virt-guest-cloud&environment_type=production' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'

```

__Payload 1__
```json
[
  {
    "package_id": 707,
    "name": "nc.xsmall",
    "bandwidth": 1000,
    "monthly_fee": 49,
    "setup_fee": 0,
    "overage_fee": 0.5,
    "bandwidth_profile_id": 2,
    "type": "virt-guest-cloud",
    "cpu_used": 0,
    "ip_num": 2,
    "form_id": 0,
    "auto_renew": "yes",
    "virt_cpu": 0,
    "virt_ram": 0,
    "virt_disk": 50,
    "default_term": 0,
    "ssl_product_code": "",
    "app_id": 0,
    "virt_dedicated_guest": 0,
    "virt_cloud_host_type_id": 1,
    "company_id": 4,
    "user_concurrency": 25,
    "user_autoscale_concurrency": 50,
    "autoscale_fee": 0,
    "environment_type": "production",
    "child_accounts": 10,
    "id": 707,
    "identity": "nc.xsmall",
    "is_real": true,
    "meta": {
      "scope": "package"
    },
    "description": "",
    "term_fee": {
      "1": 49
    },
    "effective_monthly_fee": {
      "1": 49
    },
    "terms": {
      "1": 1
    },
    "hdd_count": 0
  }
]
```

The above payload is one of the entries returned.  The `package_id` is the value you will use pass in as `package_id` when making calls to [cloud-account](CloudAccount.md).

### Types of Certificates that can be purchased

This endpoint lists the applications that can be installed on cloud accounts.

__Parameters__

| Name | Value | Type |Required |
| :--- | :--- | :---: | :---: |
| `type` | `ssl` | String | YES |
| `sortProperty` | `id` | String | YES |
| `sortDirection` | `desc` | String | YES |


__Example 2__
```shell
curl -v '__URL__/package?type=ssl&sortProperty=id&sortDirection=desc' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'

```

The payload returned is a complete list of all types of SSL certificates that can be installed. The value of `package_id` is the value used in other API endpoint calls.

__Payload 2__
```json
[
  {
    "package_id": 575,
    "name": "Wildcard SSL",
    "bandwidth": 0,
    "monthly_fee": 0,
    "setup_fee": 0,
    "overage_fee": 0.5,
    "bandwidth_profile_id": 2,
    "type": "ssl",
    "cpu_used": 0,
    "ip_num": 2,
    "form_id": 22,
    "auto_renew": "yes",
    "virt_cpu": 0,
    "virt_ram": 0,
    "virt_disk": 0,
    "default_term": 0,
    "ssl_product_code": "positivesslwildcard",
    "app_id": 0,
    "virt_dedicated_guest": 0,
    "virt_cloud_host_type_id": 0,
    "company_id": 4,
    "user_concurrency": 0,
    "user_autoscale_concurrency": 0,
    "autoscale_fee": 0,
    "environment_type": "production",
    "child_accounts": 0,
    "id": 575,
    "identity": "Wildcard SSL",
    "is_real": true,
    "meta": {
      "scope": "package"
    },
    "description": "",
    "term_fee": {
      "12": 149.95,
      "24": 225.96,
      "36": 285.96
    },
    "effective_monthly_fee": {
      "12": 149.95,
      "24": 112.98,
      "36": 95.32
    },
    "terms": {
      "12": 12,
      "24": 24,
      "36": 36
    },
    "hdd_count": 0,
    "order_form": []
  }
]
```
