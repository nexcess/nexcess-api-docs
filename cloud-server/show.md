Portal: Cloud Servers
---------------------

**since** 0.0.0

cloud-server:show
==================

Shows details of a cloud server.

**Endpoint**:  GET /v1/cloud-server/{id}

**Access**: service view permission

**Parameters**: none

**Request**:
```
curl -i "$PORTAL_API_URL/v1/cloud-server/$CLOUDSERVER_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Mon, 19 Aug 2019 02:23:34 GMT
Content-Type: application/json
Content-Length: 682
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.21
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 34076,
  "identity": "jarvis01-stg-kvm03.us-midwest-1.nexcess.net - cloud-server-example",
  "bandwidth": {
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
    "given": "2048",
    "type": "GB"
  },
  "client": { "id": 24512, "identity": "Bosco-Bradtke" },
  "cloud": { "id": 1, "identity": "us-midwest-1" },
  "control_panels": null,
  "has_console": true,
  "has_stored_password": null,
  "hostname": "cloud-server-example",
  "is_rebootable": null,
  "network": {
    "public_ip": "203.113.0.1",
    "nat_ip": "10.100.0.1",
    "private_ip": "10.200.0.1"
  },
  "os": { "id": 30, "identity": "centos 7 (x86_64)" },
  "package": { "id": 677, "identity": "nex1.small" },
  "power_status": "on",
  "server_details": {
    "cpu": 2,
    "ram": 2048,
    "disk_space": 40,
    "bandwidth": 2048
  },
  "service": { "id": 58248, "identity": "us-midwest-1 - cloud-server-example - 203.113.0.1" }
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (doesn't exist on client account): 404 Not Found
