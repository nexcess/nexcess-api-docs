Portal: Service
---------------

**since** 0.4.0

service:list
============

Lists services on an account.

**Endpoint**:  GET /v1/service

**Alternate Endpoint**:  GET /v1/service/{type}

This alternate endpoint is sugar for `GET /v1/package?filter[type]={type}`. In addition, type-specific information will be added to the response payload. When no type is specified, a generic service payload is returned.

For convenience, the following type aliases are defined:

| **alias**         | type             |
|-------------------|------------------|
| **cloud-account** | virt-guest-cloud |
| **cloud-server**  | virt-guest       |

**Access**: service view permission

**Parameters**:
- string `filter[client_id]` (optional): filters results by client id.
- string `filter[parent_id]` (optional): filters results by parent service id.
- string `filter[status]` (optional): filters results by service status (one of `enabled`|`disabled`|`suspended`).
- string `filter[state]` (optional): filters results by service state (one of `creating`|`destroying`|`failure`|`stable`|`resizing`|`installing`|`renaming`).
- string `filter[type]` (optional): filters results by service type (one of `app`|`colocation`|`dedicated`|`domain`|`eadn`|`generic`|`shared`|`shared-reseller`|`software-license`|`ssl`|`storage-object`|`vps`|`virt-guest`|`virt-guest-cloud`).
- string `filter[nickname]` (optional): filters results by client-provided nickname.
- string `filter[external_key]` (optional): filters results by client-provided key.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`client_id`|`parent_id`|`start_date`|`status`|`state`|`type`|`nickname`|`external_key`|`last_bill_date`|`next_bill_date`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$PORTAL_API_URL/v1/service" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
curl -i "$PORTAL_API_URL/v1/service" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"

HTTP/1.1 200 OK
Server: nginx
Date: Thu, 16 Jan 2020 02:59:56 GMT
Content-Type: application/json
Content-Length: 11699
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.21
Content-Range: items 1-22/22
NocWorx-Api-Version: 0.3.0
Served-By: nwdev-web01-int

[
  {
    "id": 12345,
    "identity": "cloud-account.example.com - nc.small-dev",
    "status": "enabled",
    "billing_info": {
      "type": "monthly",
      "amount": "10.00",
      "is_overdue": false,
      "last_bill_date": 0,
      "next_bill_date": 1581656400,
      "bill_day": "14",
      "auto_renew": "yes"
    },
    "cancellation_info": {
      "can_cancel": true
    },
    "client": {
      "id": 23456,
      "identity": "Sample Inc.",
      "metadata": {
        "scope": "client",
        "uri": null
      }
    },
    "external_key": "",
    "metadata": {
      "scope": "service",
      "uri": "/v1/service/cloud-account/12345/"
    },
    "nickname": "",
    "parent": null,
    "start_date": 1579010429,
    "state": "stable",
    "type": "virt-guest-cloud"
  },

  . . .

]
```

**Success Response** (with specified service type): 200 OK
```
curl -i "$PORTAL_API_URL/v1/service/$SERVICE_TYPE" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"

HTTP/1.1 200 OK
Server: nginx
Date: Thu, 16 Jan 2020 03:02:24 GMT
Content-Type: application/json
Content-Length: 6029
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.21
Content-Range: items 1-5/5
NocWorx-Api-Version: 0.3.0
Served-By: nwdev-web01-int

[
  {
    "id": 12345,
    "identity": "cloud-account.example.com - nc.small-dev",
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
      "given": "100",
      "type": "##LG_GB##"
    },
    "billing_info": {
      "type": "monthly",
      "amount": "10.00",
      "is_overdue": false,
      "last_bill_date": 0,
      "next_bill_date": 1581656400,
      "bill_day": "14",
      "auto_renew": "yes"
    },
    "cancellation_info": {
      "can_cancel": true
    },
    "child_accounts": [],
    "client": {
      "id": 23456,
      "identity": "Bosco-Bradtke",
      "metadata": {
        "scope": "client",
        "uri": null
      }
    },
    "cloud": {
      "id": 1,
      "identity": "us-midwest-1",
      "metadata": {
        "scope": "virt-cloud",
        "uri": null
      }
    },
    "cloud_accounts": [
      {
        "id": 3456,
        "identity": "cloud-account.example.com",
        "metadata": {
          "scope": "virt-guest-cloudaccount",
          "uri": "/v1/cloud-account/3456/"
        }
      }
    ],
    "containers": [],
    "dev_accounts": [],
    "environment_type": "development",
    "external_key": "",
    "ips": ["203.0.113.1"],
    "main_ip": "203.0.113.1",
    "metadata": {
      "scope": "service",
      "uri": "/v1/service/cloud-account/12345/"
    },
    "nickname": "",
    "parent": null,
    "plan_type": false,
    "settings": {
      "extranet.disable-networking.enabled": true
    },
    "staging_accounts": [],
    "start_date": 1579010429,
    "state": "stable",
    "type": "virt-guest-cloud"
  },

  . . .

]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
