# Portal: Enterprise Cloud

## enterprise-cloud:list
Lists Enterprise Cloud Services.

**Endpoint**: GET /v1/enterprise-cloud

#### Access
service view permissions

#### Input
- integer `filter[id]` (optional): filter list by system ID.
- integer `filter[parent_id]` (optional): filter list by system ID of parent Service.
- string `filter[state]` (optional): filter list by Service state.
- string `filter[status]` (optional): filter list by Service status.
- string `filter[inicknamep]` (optional): filter list by nickname.
- integer `match[id]` (optional): filter list by system ID.
- integer `match[parent_id]` (optional): filter list by system ID of parent Service.
- string `match[state]` (optional): filter list by Service state.
- string `match[status]` (optional): filter list by Service status.
- string `match[nickname]` (optional): match against nickname.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`state`|`cloud`|`package`|`deploy_date`|`deploy_complete_date`|`nickname`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request:
```
$ curl "$PORTAL_API/v1/enterprise-cloud" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response**
```
[
  {
    "id": 197139,
    "identity": "us-midwest-2 - lb-100045318.us-midwest-2.lwdns.dev - 192.190.222.56",
    "metadata": {
      "scope": "service",
      "uri": "/v1/service/cloud-server/197139"
    },
    "status": "enabled",
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
    "parent": null,
    "settings": {
      "extranet.disable-networking.enabled": true
    },
    "start_date": 1663069463,
    "state": "stable",
    "type": "virt-guest"
  },
  . . .
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
