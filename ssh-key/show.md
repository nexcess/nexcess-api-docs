Portal: Ssh Keys
----------------

**since** 0.0.0

ssh-key:show
============

Shows details of an Ssh Key.

**Endpoint**:  GET /v1/ssh-key/{id}

**Access**: logged-in users

**Parameters**: none

**Request**:
```
curl -i "$PORTAL_API_URL/v1/ssh-key/$KEY_ID" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 20 Aug 2019 17:21:07 GMT
Content-Type: application/json
Content-Length: 785
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.2.21
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{
  "id": 138,
  "identity": "stark.pub - f4:e1:75:e9:cf:83:c4:0a:83:e8:26:6b:c5:61:22:8f  user@example.com (RSA)",
  "client": { "id": 24512, "identity": "Bosco-Bradtke" },
  "creation_date": 1490204568,
  "fingerprint": "f4:e1:75:e9:cf:83:c4:0a:83:e8:26:6b:c5:61:22:8f  user@example.com (RSA)",
  "key": "ssh-rsa AAAAB3NzaC1yc2EAAAADCQABAAABAQDDixNxEbVT . . . user@example.com",
  "key_size": 2048,
  "name": "stark.pub",
  "user": { "id": 27767, "identity": "Annabel Whyman - user@nocworx.com" }
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (token_id doesn't exist on client account): 404 Not Found
