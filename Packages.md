# List Packages

***Endpoint***
```
/package?type=virt-guest-cloud&production
```

**Accepted Verbs**
- GET

## GET

This endpoint lists the applications that can be installed on cloud accounts. There are two required parameters to make a call to this endpoint.

- `type=virt-guest-cloud` `virt-guest-cloud` is an internal token specifying a type of package. Currently it is the only type that is publicly exposed.
- `environment_type=production` There are two different environment types supported by the API. For now, only use production. As the other is readied for public consumption, this documentation will be updated to describe it and it's differences.

__Example 1__
```shell
curl -v '__URL__/package?type=virt-guest-cloud&production' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'

```

__Payload 1__
```json
[
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

The above payload is one of the entries returned.  The `package_id` is the number you will use in `package_id` when making calls to [cloud-account](CloudAccount.md).