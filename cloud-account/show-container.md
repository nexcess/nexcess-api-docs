# Portal: Cloud Account

## cloud-account:show-container-details
Shows Container group info.

#### Access
container view

#### Request
```
$ curl "$PORTAL_API_URL/v1/cloud-account/{id}/container" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 24 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/cloud-account/1089/container
NocWorx-Api-Version: 0.0.0

[
  {
    "id": 4,
    "identity": "cg-4-elasticsearch.us-midwest-2",
    "metadata": {
      "scope": "virt-guest-containergroup",
      "uri": null
    },
    "status": "used",
    "addon": {
      "id": 2259,
      "identity": "nc.elasticsearch-small",
      "metadata": {
        "scope": "package-addon",
        "uri": "/v1/package/addon/2259"
      },
    "status": "web-active",
    "type": "virt-guest-cloud"
    },
    "cloud_account": {
      "id": 1089,
      "identity": "b7244b5168.1700.lwdns.dev",
      "metadata": {
        "scope": "virt-guest-cloudaccount",
        "uri": "/v1/cloud-account/1089"
      },
      "status": "used",
      "state": "stable",
      "type": "account"
    },
    "host": {
      "id": 9,
      "identity": "containerhost-1700044889.us-midwest-2.lwdns.dev",
      "metadata": {
        "scope": "virt-guest-containerhost",
        "uri": null
      },
      "status": "active",
      "type": {
        "id": 1,
        "identity": "",
        "metadata": {
          "scope": "virt-guest-containerhost-type",
          "uri": null
        },
        "type": "docker"
      }
    },
    "is_authenticated": false,
    "ports": [
      {
        "id": 2,
        "protocol": "tcp",
        "publish_port": 7295,
        "target_port": 9200
      }
    ],
    "state": "stable",
    "type": {
      "id": 11,
      "identity": "elasticsearch",
      "metadata": {
        "scope": "virt-guest-containergroup-type",
        "uri": null
      }
    },
    "version": "7.6-latest"
  }
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

