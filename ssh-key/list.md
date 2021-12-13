Portal: Ssh Keys
----------------

**since** 0.0.0

ssh-key:list
============

Lists ssh keys that belong to the logged-in user.

**Endpoint**:  GET /v1/ssh-key

**Access**: logged-in users

**Parameters**:
- `filter[name]`: Optional: filters results by key name.
- `filter[id]`: Optional: filters results by key id.
- `page`: Optional: 1-based result set count for paginated results.
- `pageSize`: Optional: maximum number of results to include per "page" of a paginated list.
- `sortBy`: Optional: field to sort the list by; one of `id`|`name`.
- `sortOrder`: Optional: sort direction; one of `ASC`|`DESC`.

**Request**:
```
curl -i "$PORTAL_API_URL/v1/ssh-key" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
[
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
    "fingerprint": "SHA256:3XTUdV3yYM/... (RSA)",
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
  },
  . . .
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
