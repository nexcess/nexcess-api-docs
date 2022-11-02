# Portal: Site

## site:logs
Checks free trial availability.

#### Access
anyone

#### Input
- email `customer_email` (optional): Customer email address
- integer `package_id` (optional): system ID of the free trial package

#### Request
```
$ curl "$PORTAL_API_URL/v1/site/free-trials" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "customer_email" : "alice@example.com",
    "package_id": 789
  }'
```

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Wed, 24 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/site/free-trials
NocWorx-Api-Version: 0.0.0

{
  "free_trials_available": true,
  "reasons": []
}
```

**Failure Response** (invalid inputs): 422 Unprocessable Entity
