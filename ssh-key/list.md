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
    "id": 138,
    "identity": "stark.pub - f4:e1:75:e9:cf:83:c4:0b:83:e8:36:6b:c5:61:22:8f  user@example.com (RSA)",
    "client": { "id": 24512, "identity": "Bosco-Bradtke" },
    "creation_date": 1490204568,
    "fingerprint": "f4:e1:75:e9:cf:83:c4:0b:83:e8:36:6b:c5:61:22:8f  user@example.com (RSA)",
    "key_size": 2048,
    "name": "stark.pub",
    "user": { "id": 27767, "identity": "Annabel Whyman - user@example.com" }
  },

  . . .
]
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable

**Failure Response** (other bad input): 422 Unprocessable Entity
