# Portal: Cloud Account

## cloud-account:sso-url
Get Sso Url.

#### Access
cloud account view

#### Input
- integer `id` (required): System ID of the sso url.

#### Request
```
$ curl "$PORTAL_API_URL/v1/cloud-account/{id}/sso-url" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 22 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/cloud-account/1234/sso-url
NocWorx-Api-Version: 0.0.0

{
  "siteworx_url": "https://192.190.222.73:2443/siteworx/index?action=sso&sid=kmbk8krtn6oaibm0k1q6rb6qqc&uri=L3NpdGV3b3J4L292ZXJ2aWV3",
  "phpmyadmin_url": "https://192.190.222.73:2443/siteworx/index?action=sso&sid=g6stj7sc185nu47q7itmd6n0nj&uri=L3NpdGV3b3J4L215c3FsL3BocG15YWRtaW4=",
  "awstats_url": "https://192.190.222.73:2443/siteworx/index?action=sso&sid=d1u6egs0ia6r1ekdedt1nvvbvm&uri=L3NpdGV3b3J4L3N0YXRzL2F3c3RhdHM="
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
