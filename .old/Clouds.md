# List Clouds

**End Point**
```
/virt-cloud
```
**Accepted Verbs**
- GET

## GET

This endpoint lists the applications that can be installed on cloud accounts. There are no required parameters to make a call to this endpoint.

__Example 1__
```shell
curl -v '__URL__/virt-cloud' \
  -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
  -H 'Accept: application/json'

```

__Payload 1__
```json
[
  {
    "id": 1,
    "identity": "us-midwest-1",
    "is_real": true,
    "meta": {
      "scope": "virt-cloud"
    },
    "type": "openstack",
    "status": "active",
    "location": "Southfield, MI",
    "location_code": "us-midwest-1",
    "country": "US"
  }
]
```

The above payload is one of the entries returned.  The `id` is the value you will pass in as `cloud_id` when making calls to [cloud-account](CloudAccount.md).

