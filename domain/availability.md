# Portal: Domain

## domain:availability-lookup
Looks up registration availability for a given domain.

#### Access
public

#### Request
```
$ curl "$PORTAL_API_URL/v1/domain/availability/{$DOMAIN_NAME_WITH_OR_WITHOUT_TLD}" \
  -H "Accept: application/json"
```
_If the submitted domain name does not include a TLD, the response will still include `alternatives` but the top-level `domain` property will be `null`._

#### Responses
**Success Response** (success): 200 OK
```
HTTP/1.1 200 OK
Date: Tue, 02 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
NocWorx-Api-Version: 0.0.0

{
  "domain": {
    "domain": "example.com",
    "is_available": false,
    "tld": {
      "id": 1234,
      "identity": "com",
      "metadata": { "scope": "domain-tld", "uri": null }
    },
    "package": {
      "id": 5678,
      "identity": "Domain Registration - .com",
      "metadata": { "scope": "package", "uri": "/v1/package/domain/5678" }
    },
    "pricing": [
      {
        "term": { "months": 12, "display": "1 year" },
        "price": "15.99"
      },
      {
        "term": { "months": 24, "display": "2 years" },
        "price": "29.95"
      },
      . . .
    ]
  },
  "alternatives": [
    {
      "domain": "example.net",
      "is_available": false,
      "tld": {
        "id": 2345,
        "identity": "net",
        "metadata": { "scope": "domain-tld", "uri": null }
      },
      "package": {
        "id": 6789,
        "identity": "Domain Registration - .net",
        "metadata": { "scope": "package", "uri": "/v1/package/domain/6789" }
      },
      "pricing": [
        {
          "term": { "months": 12, "display": "1 year" },
          "price": "15.99"
        },
        . . .
      ]
    },
    . . .
  ]
}
```

**Failure Response** (domain name is invalid or cannot be parsed): 422 Unprocessable Entity
