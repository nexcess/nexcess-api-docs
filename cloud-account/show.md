Portal: Cloud Accounts
----------------------

**since** 0.0.0

cloud-account:show
==================

Shows details of a cloud account.

**Endpoint**:  GET /v1/cloud-account/{id}

**Access**: service view permission

**Parameters**: none

**Request**:
```
curl -i "$PORTAL_API_URL/v1/cloud-account/$CLOUDACCOUNT_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 17 Jul 2019 01:58:05 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 879
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.15
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 976,
  "identity": "cloud-account.example.org",
  "state": "stable",
  "domain": "cloud-account.example.org",
  "temp_domain": "fe22c8ad4e.nxcli.net",
  "ip": "203.0.113.1",
  "service": { "id": 58246, "identity": "cloud-account.example.org - nc.small" },
  "app": { "id": 14, "identity": "Flexible" },
  "cloud": { "id": 1, "identity": "us-midwest-1" },
  "package": { "id": 716, "identity": "nc.small" },
  "deploy_date": 1556138113,
  "deploy_complete_date": 1556138138,
  "cloudhost": { "id": 34076, "identity": "jarvis01-stg-kvm02.us-midwest-1.nexcess.net - cloudhost-100044793.us-midwest-1.nxswd.net" },
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
        "socket": "/var/run/redis-multi-a970201d.redis/redis.sock",
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
    "access": {}
  },
  "project": { "id": 461, "identity": "cloud-account.example.org" },
  "is_dev_account": false,
  "reference_account": null,
  "parent_account": null,
  "ssl_cert": null
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
