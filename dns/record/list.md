# Portal: DNS Records

## dns-zone:list
List DNS records.

#### Access
dns record view

#### Input
- integer `filter[id]` (optional): filter list by system ID
- integer `filter[type]` (optional): filter list by record type
- integer `filter[zone_id]` (optional): filter list by DNS zone id
- integer `match` (optional): match against id, type, zone_id value
- integer `range` (optional): find id values within .. range
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): sort list by id, type, zone_id.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/dns/zone/$ZONE_ID/record" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 12 Jan 2022 14:17:26 GMT
Content-Type: application/json
Transfer-Encoding: chunked
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.4.3
Content-Range: items 1-16/16
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

[
  {
    "id": 166730,
    "identity": "magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166730"
    },
    "host": "",
    "target": "ns1.nexcess.net",
    "ttl": 86400,
    "type": "NS",
    "update_date": 1595850600
  },
  {
    "id": 166731,
    "identity": "magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166731"
    },
    "host": "",
    "target": "ns2.nexcess.net",
    "ttl": 86400,
    "type": "NS",
    "update_date": 1595850600
  },
  {
    "id": 166732,
    "identity": "magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166732"
    },
    "host": "",
    "target": "ns3.nexcess.net",
    "ttl": 86400,
    "type": "NS",
    "update_date": 1595850601
  },
  {
    "id": 166733,
    "identity": "magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166733"
    },
    "host": "",
    "target": "ns4.nexcess.net",
    "ttl": 86400,
    "type": "NS",
    "update_date": 1595850601
  },
  {
    "id": 166734,
    "identity": "magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166734"
    },
    "host": "",
    "target": "208.69.126.196",
    "ttl": 900,
    "type": "A",
    "update_date": 1595850603
  },
  {
    "id": 166735,
    "identity": "www.magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166735"
    },
    "host": "www",
    "target": "magento.com",
    "ttl": 1800,
    "type": "CNAME",
    "update_date": 1595850603
  },
  {
    "id": 166736,
    "identity": "ftp.magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166736"
    },
    "host": "ftp",
    "target": "magento.com",
    "ttl": 1800,
    "type": "CNAME",
    "update_date": 1595850604
  },
  {
    "id": 166737,
    "identity": "ssh.magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166737"
    },
    "host": "ssh",
    "target": "magento.com",
    "ttl": 1800,
    "type": "CNAME",
    "update_date": 1595850604
  },
  {
    "id": 166738,
    "identity": "mail.magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166738"
    },
    "host": "mail",
    "target": "208.69.126.196",
    "ttl": 1800,
    "type": "A",
    "update_date": 1595850604
  },
  {
    "id": 166739,
    "identity": "magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166739"
    },
    "host": "",
    "target": "10 mail.magento.com",
    "ttl": 1800,
    "type": "MX",
    "update_date": 1595850605
  },
  {
    "id": 166740,
    "identity": "_imap._tcp.magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166740"
    },
    "host": "_imap._tcp",
    "target": "0 0 0 .",
    "ttl": 1800,
    "type": "SRV",
    "update_date": 1595850605
  },
  {
    "id": 166741,
    "identity": "_imaps._tcp.magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166741"
    },
    "host": "_imaps._tcp",
    "target": "0 1 993 mail.magento.com",
    "ttl": 1800,
    "type": "SRV",
    "update_date": 1595850606
  },
  {
    "id": 166742,
    "identity": "_pop3._tcp.magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166742"
    },
    "host": "_pop3._tcp",
    "target": "0 0 0 .",
    "ttl": 1800,
    "type": "SRV",
    "update_date": 1595850606
  },
  {
    "id": 166743,
    "identity": "_pop3s._tcp.magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166743"
    },
    "host": "_pop3s._tcp",
    "target": "0 1 995 mail.magento.com",
    "ttl": 1800,
    "type": "SRV",
    "update_date": 1595850607
  },
  {
    "id": 166744,
    "identity": "magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166744"
    },
    "host": "",
    "target": "v=spf1 +a +mx +ip4:208.69.126.196 include:relay.mailchannels.net ~all",
    "ttl": 1800,
    "type": "TXT",
    "update_date": 1595850607
  },
  {
    "id": 166745,
    "identity": "default._domainkey.magento.com",
    "metadata": {
      "scope": "dns-record",
      "uri": "/v1/dns/reverse/166745"
    },
    "host": "default._domainkey",
    "target": "v=DKIM1; k=rsa; p=MIIBIjANBgkqhkiG9w0BAQEFAAOCAQ8AMIIBCgKCAQEAuXv6cOhVvPtzsMJUHz7Q62N6JH1U0Bc2ZAOOVOMUZLMxE2jjEh3o65NUauTZ84nY0QDZFWMP8hjeDv5Pv2gUvzYbz0HRiJ4HeqkSdMLjDfhsuIE4gjVHOq5+EuNtrkR3D306SQjTit1moV1RWOQGOx1gd9aAnQavEj7Ls9HIB3gBXoh0HBN5PtBsW/Ye4OHOmQzNqURohbxY0pVi5rs5SfVpFJHyQ9IO6CUyAjG4sUtt/JuhpUmPYw4W8uHqNnIQcqCSUhkXM4b9vZEe3nHExDVlqA+k6+nYVI4EaRemx8+rboELhAj/U5NytQIq5i0NYIT1GFpJi3oGT00/aqqrLwIDAQAB;",
    "ttl": 1800,
    "type": "TXT",
    "update_date": 1595850608
  }
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
