Admin: Launcher
---------------

**since** 0.2.0

launch:as-client
================

Proxies a Portal Api endpoint, using admin auth and then performing the request as the specified client+user. The response returned will be from the Portal Api, as though the Client User made the request directly.

**Endpoint**: GET|POST|DELETE /v1/as-client/{__client_id}/{__client_user_id}/{__client_uri}

**Alternate Endpoint**: GET|POST|DELETE /v1/as-client/{__client_id}/{__client_uri}

The alternate endpoint is a shorthand for specifying the Client account's owner as the Client User, and will serve identical responses.

**Parameters**:
- integer `__client_id` (required): Serial id of the client account to launch
- integer `__client_user_id` (optional): Serial id of the Client User to authenticate+authorize as. Omit to use the client account owner
- string `__client_uri` (required): The portal endpoint to proxy to, as a portal api root-relative URI (that is, the version prefix must be included)

Additionally, all inputs required by the portal endpoint must be provided.

**Request**:
```
curl -i "$ADMIN_API_URL/v1/as-client/$CLIENT_ID/$CLIENT_URI" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Accept: application/json"
```
```
curl -i -X POST "$ADMIN_API_URL/v1/as-client/$CLIENT_ID/$CLIENT_URI" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d $CLIENT_URI_INPUTS
```
```
curl -i -X DELETE "$ADMIN_API_URL/v1/as-client/$CLIENT_ID/$CLIENT_URI" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Accept: application/json"
```

**Success Response**: Returns the Portal Api response, unmodified

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity

**Failure Response** (other): Returns the Portal Api failure response, unmodified
