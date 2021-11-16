# Portal: Client

## client:feedback-sso
SSO info for customer feedback.

#### Access
client view

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/client/feedback-sso" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 15 Nov 2021 12:51:27 GMT
Content-Length: 44
NocWorx-Api-Version: 0.0.0

{
  "app_id":"5b324f...",
  "token":"eyJ0eXA...VeryLongToken...1_L4XYlw",
  "boards":[
    {
      "created":"2018-06-26T13:43:01.478Z",
      "id":"5b324f...",
      "isPrivate":false,
      "name":"Ideas",
      "postCount":180,
      "token":"123e4567-e89b-12d3-a456-426614174000",
      "url":"ideas"
    }
  ]
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
