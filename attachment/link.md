# Portal: Attachment

## attachment:link
Shows the link to download an attachment, including token.

#### Access
attachment link view

#### Request
```
$ curl -i -X GET "$PORTAL_API_URL/v1/attachment/{id}/download-link" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Thur, 28 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/attachment/54/download-link
NocWorx-Api-Version: 0.0.0

{
  "attachment": {
    "id": 54,
    "identity": "30talks.png",
    "metadata": {
      "scope": "attachment",
      "uri": "/v1/attachment/54/download-link"
    }
  },
  "download_link": "https://portal.test.nxswd.net/attachment/54.download?token=eyJ0eXAiOiJKV1QiLCJhbGciOiJIUzI1NiJ9.eyJ2ZXIiOiIyIiwiaWF0IjoxNjM1NDI3MDU2LCJqdGkiOiJmOTUyMzkxYi0yYTg0LTRmYTctOTc2My0xNGQ0YmZhMjQxN2QiLCJzdWIiOiJ7XCJleHRyYW5ldFwiOntcImNsaWVudFwiOjM4MTE0LFwidXNlclwiOjYxNDIwfX0iLCJleHAiOjE2MzU0MjczNTYsImFsdiI6MiwicnNyYyI6WyJHRVQgYXR0YWNobWVudFwvNTQuZG93bmxvYWQiXX0.ddNfJAipwewpEwEefbmwSOQ0RLqg-vmjDS-W-Yi_KmY"
}
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
