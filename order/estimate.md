# Portal: Order

## order:estimate
Estimates total charges, taxes, and discounts for a given Order.

Pricing returned is not a guarantee and may change based on authentication status, address, order history, date/time of order, and other factors.
For best results, requests should be authenticated and be made as close to the time of order as possible.

#### Access
None (public)

#### Input
- array `address` (optional): Billing address for the Order; defaults to the customer's invoice address if not provided. _see address:add inputs._
- string[] `discounts` (optional): A list of Discount codes to apply to the Order. These are applied to Order items in a first-come, first-served approach.
- array[] `items` (required): A list of items to order:
  - _for all item types_:
    - string `order_type` (required): One of `app`|`colocation`|`dedicated`|`domain`|`eadn`|`generic`|`shared`|`shared-reseller`|`software-license`|`ssl`|`storage-object`|`vps`|`plan`|`cloud-server`|`virt-guest`|`virt-guest-cloud`|`virt-guest-volume`
    - string `nickname` (optional): A customer-chosen identifier for the Order.
    - int `package_id` (required): The system ID of the Package to order.
    - int `term` (required): The purchase term (in months).
    - array[] `addons` (optional): A list of Package Addons to order:
      - int `addon_id` (required): The system ID of the Addon.
      - int `quantity` (required): The quantity of Addons to add to the Order.
  - _for domains_:
    - string `order_type` (required): `domain`
    - int `package_id` (optional): If omitted, Package will be determined by the domain TLD.
    - string `domain_name` (required): The domain name, with or without TLD, to order.
    - int `tld_id` (required if `domain_name` omits TLD): The system ID of the TLD to order.
    - array[] `contact` (optional): Whois Contact information to use. If omitted, the Client's "technical" contact information will be used. _see address:add inputs._
  - _for plans_:
    - string `order_type` (required): `plan`|`virt-guest-cloud`
    - int `app_id` (required): The system ID of the app to install.
    - int `cloud_id` (required): The system ID of the desired service location.
    - string `domain` (optional): The domain name to set up for the new Site.
    - boolean `install_app` (optional): Install the selected app (as opposed to only setting up for install)? Defaults to `true`.
    - string `password` (optional):
    - int[] `ssh_key_ids` (optional): A list of systems IDs of the Ssh Keys to add to the Plan.
  - _for dev/staging plans_:
    - string `ref_type` (required): One of `development`|`staging`
    - boolean `copy_account` (optional): Copy data from the source Site?
    - int `ref_cloud_account_id` (optional): System ID of the source Site.
    - int `ref_service_id` (optional): System ID of the source Plan.
    - boolean `scrub_account` (optional): Anonymize data copied from the source Site?
    - boolean `scrub_users` (optional): Remove user accounts copied from the source Site?

#### Request
```
$ curl -X POST "$PORTAL_API/v1/order/estimate" \
  -H "Authorization: Bearer $PORTAL_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "discounts": ["DISCEX10", "BADCOUPON5"],
    "items": [
      {"order_type":"plan","term":1,"addons":[{"id":2259,"quantity":1}],"package_id":707,"cloud_id":4,"app_id":12},
      {"order_type":"domain","term":12,"domain_name":"example.com"}
    ]
  }'
```

#### Responses
**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Date: Mon, 15 Nov 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/cloud-account/1091/php-version
NocWorx-Api-Version: 0.6.0

{
  "items": [
    {
      "package": {
        "id": 707,
        "identity": "nc.xsmall",
        "metadata": {
          "scope": "package",
          "uri": "/v1/package/site/707"
        },
        "status": "web-active",
        "type": "virt-guest-cloud"
      },
      "price": "29.00",
      "term": 1,
      "addons": [
        {
          "addon": {
            "id": 2259,
            "identity": "nc.elasticsearch-small",
            "metadata": {
              "scope": "package-addon",
              "uri": "/v1/package/addon/2259"
            },
            "status": "web-active",
            "type": "virt-guest-cloud"
          },
          "quantity": 1,
          "price": "20.00"
        }
      ],
      "tax": "3.68",
      "sub": "39.00",
      "total": "39.00",
      "discount": [
        {
          "code": "DISCEX10",
          "description": "DISCEX10 ($10.00)",
          "amount": "10.00"
        }
      ]
    },
    {
      "package": {
        "id": 143,
        "identity": "Domain Registration - .com",
        "metadata": {
          "scope": "package",
          "uri": "/v1/package/domain/143"
        },
        "status": "web-active",
        "type": "domain"
      },
      "price": "15.00",
      "term": 12,
      "addons": [],
      "tax": "1.13",
      "sub": "15.00",
      "total": "15.00",
      "discount": []
    }
  ],
  "subtotal": "54.00",
  "tax": "4.81",
  "total": "58.81",
  "total_discount": "10.00"
}
```
**Failure Response** (bad input): 422 Unprocessable Entity
