# Portal: Payment

## payment:list
Lists Invoices.

#### Access
payment view

#### Input
- integer `filter[id]` (optional): filter list by system ID.
- string `match[id]` (optional): match against system ID.
- string `range[id]` (optional): find system IDs within "{min}..{max}" range.
- integer `page` (optional): 1-based result set count for paginated results.
- integer `pageSize` (optional): maximum number of results to include per "page" of a paginated list.
- string `sortBy` (optional): field to sort the list by; one of `id`|`invoice_id`|`amount`|`original_amount`|`payment_date`|`type`|`reference`|`credit_id`|`date`|`invoice`.
- string `sortOrder` (optional): sort direction; one of `ASC`|`DESC`.status

#### Request
```
$ curl -i "$PORTAL_API_URL/v1/payment" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json"
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 29 Dec 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

[]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (other bad input): 422 Unprocessable Entity

**Failure Response** (bad range/page number/page size): 416 Requested Range Not Satisfiable
