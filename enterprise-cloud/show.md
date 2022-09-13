# Portal: Enterprise Cloud

## enterprise-cloud:show
Shows details of an Enterprise Cloud Service, its Cluster, and Nodes.

**Endpoint**: GET /v1/enterprise-cloud/{cluster_id}

#### Access
service view permissions

#### Input
none

#### Request:
```
$ curl "$PORTAL_API/v1/enterprise-cloud/$CLUSTER_ID" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response**
```
{
  "id": 197139,
  "identity": "us-midwest-2 - lb-100045318.us-midwest-2.lwdns.dev - 192.190.222.56",
  "metadata": {
    "scope": "service",
    "uri": "/v1/service/cloud-server/197139"
  },
  "status": "enabled",
  "addons": [],
  "bandwidth_info": {
    "used": {
      "total": 0,
      "billable": 0
    },
    "projected": {
      "total": 0,
      "billable": 0
    },
    "previous": {
      "total": 0,
      "billable": 0
    },
    "given": "0",
    "type": "##LG_GB##"
  },
  "billing_info": {
    "type": "monthly",
    "term": 1,
    "amount": "0.00",
    "is_overdue": false,
    "last_bill_date": 1663069463,
    "next_bill_date": 1665633600,
    "bill_day": "13",
    "auto_renew": "yes"
  },
  "cancellation_info": {
    "can_cancel": true
  },
  "cloud": {
    "id": 4,
    "identity": "us-midwest-2",
    "metadata": {
      "scope": "virt-cloud",
      "uri": null
    },
    "status": "active",
    "type": "openstack"
  },
  "cloud_servers": [
    {
      "id": 34435,
      "identity": "jarvis01-dev-kvm05.p01s02.lan3.us-midwest-2 - lb-100045318.us-midwest-2.lwdns.dev",
      "metadata": {
        "scope": "virt-guest",
        "uri": "/v1/cloud-server/34435"
      },
      "status": "used",
      "type": "kvm"
    },
    {
      "id": 34436,
      "identity": "jarvis01-dev-kvm03.p01s02.lan3.us-midwest-2 - fs-100045319.us-midwest-2.lwdns.dev",
      "metadata": {
        "scope": "virt-guest",
        "uri": "/v1/cloud-server/34436"
      },
      "status": "used",
      "type": "kvm"
    },
    {
      "id": 34437,
      "identity": "jarvis01-dev-kvm03.p01s02.lan3.us-midwest-2 - fs-100045320.us-midwest-2.lwdns.dev",
      "metadata": {
        "scope": "virt-guest",
        "uri": "/v1/cloud-server/34437"
      },
      "status": "used",
      "type": "kvm"
    }
  ],
  "cloud_status": "active",
  "contract": null,
  "discount": null,
  "external_key": "",
  "ips": [
    "192.190.222.56",
    "10.71.16.23",
    "192.190.222.119",
    "10.71.16.25",
    "192.190.222.95",
    "10.71.16.29"
  ],
  "main_ip": "192.190.222.56",
  "nickname": "Enterprise Cloud Cluster",
  "order": {
    "id": 40836,
    "identity": "(40836) Rosco-Bosco",
    "metadata": {
      "scope": "order",
      "uri": "/v1/order/40836"
    },
    "status": "allocated",
    "type": "virt-guest"
  },
  "package": {
    "id": 812,
    "identity": "Enterprise Cloud Cluster",
    "metadata": {
      "scope": "package",
      "uri": "/v1/package/cloud-server/812"
    },
    "status": "web-active",
    "type": "virt-guest"
  },
  "parent": null,
  "paypal_subscription_info": {
    "can_subscribe": false
  },
  "settings": {
    "extranet.disable-networking.enabled": true
  },
  "start_date": 1663069463,
  "state": "stable",
  "type": "virt-guest"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
