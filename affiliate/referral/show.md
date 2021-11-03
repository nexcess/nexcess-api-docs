# Portal: Affiliate

## affiliate:show
Show Affiliate Referrals.

#### Access
affiliate referral view

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/affiliate/referral/{id}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (request was accepted for processing): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 03 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/affiliate/referral/{id}
NocWorx-Api-Version: 0.0.0

{
  "status": "active",
  "referred_date": 1272254400
}"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found

**Failure Response** (other bad input): 422 Unprocessable Entity
