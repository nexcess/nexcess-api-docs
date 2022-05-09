# Portal: DNS Reverse Records

## dns-reverse:list
Lists Reverse Dns Records

#### Access
dns reverse view

#### Input
- integer `filter[id]` (optional): filter list by system ID
- integer `match` (optional): match against id, type, zone_id value
- integer `range` (optional): find id values within .. range
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): sort list by id, host, target.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/dns/reverse" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Wed, 12 Jan 2022 14:46:13 GMT
Content-Type: application/json
Content-Length: 2
Keep-Alive: timeout=5
X-Powered-By: PHP/7.4.3
Content-Range: items 0-0/0
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
