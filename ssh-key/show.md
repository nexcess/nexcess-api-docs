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
  "id": 139,
  "identity": "nexcess-ssh-key - SHA256:3XTUdV3yYM/... (RSA)",
  "metadata": {
    "scope": "user-ssh-key",
    "uri": "/v1/ssh-key/139"
  },
  "client": {
    "id": 38114,
    "identity": "Howell Inc",
    "metadata": {
      "scope": "client",
      "uri": null
    },
    "status": "active"
  },
  "creation_date": 1638366250,
  "fingerprint": "SHA256:3XTUdV3yYM/42K7a9ZP4V/XPUmeXO2/6PX1q8Ml3Mws chittaranjanbehera@it-HP-ProBook-440-G7 (RSA)",
  "key_size": 2048,
  "name": "nexcess-ssh-key",
  "user": {
    "id": 61420,
    "identity": "Annabel Whyman - user@example.com",
    "metadata": {
      "scope": "user",
      "uri": "/v1/user/61420"
    }
  }
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (token_id doesn't exist on client account): 404 Not Found
