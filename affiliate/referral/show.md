# Portal: Affiliate

## affiliate:show
Show Affiliate Referrals.

#### Access
affiliate referral view

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/affiliate/referral/$REFERRAL_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 03 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

{
  "id": 36673,
  "identity": "Jacobs, Conn and Steuber",
  "metadata": {
    "scope": "client",
    "uri": null
  },
  "status": "active",
  "referred_date": 1462343023,
  "services": [
    {
      "id": 53721,
      "identity": "M-SIP-100 - 104.207.225.74: beyondgallery.com",
      "metadata": {
        "scope": "service",
        "uri": "/v1/service/shared/53721"
      },
      "status": "enabled",
      "state": "stable",
      "type": "shared"
    }
  ]
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
