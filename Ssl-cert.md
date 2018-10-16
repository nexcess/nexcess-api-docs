# SSL-Cert

**End Point**

```
/ssl-cert
```
The `/ssl-cert` endpoint allows you to Install, retrieve and remove SSL certificates attached to the account holding the API key.

**Accepted Verbs**

- GET
  - [List all certificates](#list-all-certificates)
  - [Retrieve a certificate](#retrieve-a-certificate)
  - [Retrieve a certificate by `service_id`](#retrieve-a-certificate-by-service_id)
- POST
  - [Import a certificate](#import-a-certificate)
  - [Create a certificate](#create-a-certificate)
- Delete
  - [Delete a certificate](#delete-a-certificate)

## GET

### List all certificates

To retrieve all the information about all the certificates associated with an account, GET the `ssl-cert` endpoint without specifying a specific CERT_ID.

__Example 1__
```shell
curl -v '__URL__/ssl-cert' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json'
```

This will return a payload contains all of the certificates associated with the account.

__Payload 1__
```json
[
  {
    "cert_id": XXX,
    "common_name": "site1.example.com",
    "client_id": XXXXX,
    "broker_id": 1,
    "valid_from_date": 0,
    "valid_to_date": 0,
    "chain_crts": "",
    "approver_email": "postmaster@example.com",
    "alt_domains": "",
    "duns": "",
    "incorporating_agency": "",
    "id": 595,
    "identity": "site1.example.com",
    "is_real": true,
    "meta": {
      "scope": "ssl-cert"
    },
    "crt": "",
    "domain_count": 1,
    "is_multi_domain": false,
    "is_wildcard": false,
    "is_installable": false,
    "is_expired": true,
    "alt_names": [],
    "service": {
      "id": XXXXX,
      "identity": "SSL Certificate - site1.example.com",
      "is_real": true,
      "meta": {
        "scope": "service"
      },
      "type": "ssl",
      "status": "enabled",
      "description": "SSL Certificate - site1.example.com",
      "nickname": "",
      "next_bill_date": 1569297600,
      "package": {
        "id": XXX,
        "identity": "SSL Certificate",
        "is_real": true,
        "meta": {
          "scope": "package"
        },
        "type": "ssl",
        "status": "web-active"
      }
    }
  },
  {
    "cert_id": XXX,
    "common_name": "site2.example.com",
    "client_id": XXXXX,
    "broker_id": 0,
    "valid_from_date": 1480291200,
    "valid_to_date": 1574985599,
    "chain_crts": "",
    "approver_email": "",
    "alt_domains": "site2.example.com.com,www.site2.example.com",
    "duns": "",
    "incorporating_agency": "",
    "id": XXX,
    "identity": "site2.example.com",
    "is_real": true,
    "meta": {
      "scope": "ssl-cert"
    },
    "crt": "-----BEGIN CERTIFICATE-----\nMIIGbDCCBVSgAwIBAgIQfpsSGBm0aOWQUqAGPoxrizANBgkqhkiG9w0BAQsFADCB\n..Many more lines that look like this...\nBF0NmdzLYocu9erTF0vcqvRzDkwtgI5bnkBDBKA1M0MorbKDvhZz/6otapZU94qx\nK7Iorb/mh+2WFokKTzqVzTup+D3+BFKFHc3giy0zLKf0uzOzGtIoWB72vuJh04fM\ngInCCoyPSIRMKy1l84XmzgFV065g3kqxHCK8O0jpkFWgF2xbZBJCj0tWnNaWXPId\ndf6VNFF4+x1ub1x92UZ6ag==\n-----END CERTIFICATE-----",
    "domain_count": 2,
    "is_multi_domain": true,
    "is_wildcard": false,
    "is_installable": true,
    "is_expired": false,
    "alt_names": [
      "site2.example.com",
      "site2.example.com"
    ]
  }
]
```

The payload returned is a JSON encoded array of certificates.

### Retrieve a certificate

The API can return the data for a single certificate as well as [List all certificates](#list-all-certificates). To retrieve a single certificate, append the `cert_id` to the end of the URL.

__Example 2__
```shell
curl -v '__URL__/ssl-cert/CERT_ID' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json'
```

The payload returned in a JSON encoded certificate object.

__Payload 2__
```json
{
  "cert_id": XXX,
  "common_name": "site2.example.com",
  "client_id": XXXXX,
  "broker_id": 0,
  "valid_from_date": 1480291200,
  "valid_to_date": 1574985599,
  "chain_crts": "",
  "approver_email": "",
  "alt_domains": "site2.example.com.com,www.site2.example.com",
  "duns": "",
  "incorporating_agency": "",
  "id": XXX,
  "identity": "site2.example.com",
  "is_real": true,
  "meta": {
    "scope": "ssl-cert"
  },
  "crt": "-----BEGIN CERTIFICATE-----\nMIIGbDCCBVSgAwIBAgIQfpsSGBm0aOWQUqAGPoxrizANBgkqhkiG9w0BAQsFADCB\n..Many more lines that look like this...\nBF0NmdzLYocu9erTF0vcqvRzDkwtgI5bnkBDBKA1M0MorbKDvhZz/6otapZU94qx\nK7Iorb/mh+2WFokKTzqVzTup+D3+BFKFHc3giy0zLKf0uzOzGtIoWB72vuJh04fM\ngInCCoyPSIRMKy1l84XmzgFV065g3kqxHCK8O0jpkFWgF2xbZBJCj0tWnNaWXPId\ndf6VNFF4+x1ub1x92UZ6ag==\n-----END CERTIFICATE-----",
  "domain_count": 2,
  "is_multi_domain": true,
  "is_wildcard": false,
  "is_installable": true,
  "is_expired": false,
  "alt_names": [
    "site2.example.com",
    "site2.example.com"
  ]
}
```

### Retrieve a certificate by `service_id`

When a certificate is created the API endpoint returns a Service object, not a certificate object in the payload. This is because the process of creating a certificate is an out-of-bandwidth process. To check the status of the certificate, poll this endpoint. When the certificate is complete and ready for use, this endpoint's payload will contain a ssl-cert object.

>All parameters passed into `curl` on the url **must** be URLEncoded. In the example below [ and ] are urlencoded to %5B and %5D respectively.

__Example 3__
```shell
curl -v '__URL__/ssl-cert/?filter%5Bservice_id%5D=SERVICE_ID \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json'
```

The payload returned is a list of exactly one certificate object that matched the `service_id` passed in on the URL.

__Payload 3__
```json

[
  {
    "cert_id": XXXXX,
    "common_name": "example.com",
    "client_id": XXXXX,
    "broker_id": 1,
    "valid_from_date": 0,
    "valid_to_date": 0,
    "chain_crts": "",
    "approver_email": "admin@example.com",
    "alt_domains": "",
    "duns": "",
    "incorporating_agency": "",
    "id": XXXXX,
    "identity": "example.com",
    "is_real": true,
    "meta": {
      "scope": "ssl-cert"
    },
    "crt": "",
    "domain_count": 1,
    "is_multi_domain": false,
    "is_wildcard": false,
    "is_installable": false,
    "is_expired": true,
    "alt_names": [],
    "service": {
      "id": XXXXX,
      "identity": "SSL Certificate - example.com",
      "is_real": true,
      "meta": {
        "scope": "service"
      },
      "type": "ssl",
      "status": "enabled",
      "description": "SSL Certificate - example.com",
      "nickname": "",
      "next_bill_date": 1570507200,
      "package": {
        "id": 179,
        "identity": "SSL Certificate",
        "is_real": true,
        "meta": {
          "scope": "package"
        },
        "type": "ssl",
        "status": "web-active"
      }
    }
  }
]
```


## POST

### Import a certificate
To import an existing cert/key combination, the following parameters have to be supplied.

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
|`crt`| The certificate | String | YES |
|`key`| The private key | String | YES |
|`chain_cert`| Additional chain certificate | String | NO |

Unlike other endpoints that take parameters, these three parameters are very large and specifically formatted. The key and the certificates have to be JSON encoded to be submitted.

**The sample below is for experimental purposes only. Do not store keys or certificates in script files.**

In this sample shell script, all three parameters are defined as variables. They have been edited for brevity. Substitute valid keys and certificates before attempting to run the script.

Below the definition of the variables is where they are individually JSON encoded.

>Most programming languages provide for encoding and decoding of JSON payloads. The examples presented in this documentation however, are are Linux shell scripts. The Linus shell does not contain functions for manipulating JSON. There are many possible solutions to choose from. The one chosen was chosen because PHP is installed on most computers therefore it is the most likely to work.

Finally, in the `--data-binary` section of the curl call, the three variables are assembled into the final JSON payload.

__Example 4__
```shell
#!/bin/bash
CHAIN="-----BEGIN CERTIFICATE-----
MIIGCDCCA/CgAwIBAgIQKy5u6tl1NmwUim7bo3yMBzANBgkqhkiG9w0BAQwFADCB
         ...Many more lines that look like that...
lBlGGSW4gNfL1IYoakRwJiNiqZ+Gb7+6kHDSVneFeO/qJakXzlByjAA6quPbYzSf
+AZxAeKCINT+b72x

-----END CERTIFICATE-----"
CRT="-----BEGIN CERTIFICATE-----
MIIGbDCCBVSgAwIBAgIQfpsSGBm0aOWQUqAGPoxrizANBgkqhkiG9w0BAQsFADCB
         ...Many more lines that look like that...
gInCCoyPSIRMKy1l84XmzgFV065g3kqxHCK8O0jpkFWgF2xbZBJCj0tWnNaWXPId
df6VNFF4+x1ub1x92UZ6ag==
-----END CERTIFICATE-----"

KEY="-----BEGIN PRIVATE KEY-----
MIIJQwIBADANBgkqhkiG9w0BAQEFAASCCS0wggkpAgEAAoICAQCliHpsXji5TOQZ
        ...Many MANY more lines that look like that...
mWvRtmCdwO45XMKPLkglubG/PS/GEgXOscvT0mjExPAE+zHmnEShgN3Ph8ex2O2U
WS4xRl9VsWExMgBcPlqbUS/Uez+XTAw=
-----END PRIVATE KEY-----"

KEY=$(echo "$KEY" | php -r 'echo json_encode(file_get_contents("php://stdin"));' )
CRT=$(echo "$CRT" | php -r 'echo json_encode(file_get_contents("php://stdin"));' )
CHAIN=$(echo "$CHAIN" | php -r 'echo json_encode(file_get_contents("php://stdin"));' )

curl -v '__URL__/ssl-cert' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json' \
     --data-binary '{"chain_cert": '"$CHAIN"', "crt": '"$CRT"', "key": '"$KEY"'}'
```

When properly encoded valid data is transmitted to the endpoint, the return payload will contain the newly created certificate record ready to be attached to a cloud account.

__Payload 4__
```json

{
  "cert_id": XXX,
  "common_name": "example.com",
  "client_id": 38111,
  "broker_id": 0,
  "valid_from_date": 1480291200,
  "valid_to_date": 1574985599,
  "chain_crts": "",
  "approver_email": "",
  "alt_domains": "example.com,www.example.com",
  "duns": "",
  "incorporating_agency": "",
  "id": XXX,
  "identity": "example.com",
  "is_real": true,
  "meta": {
    "scope": "ssl-cert"
  },
  "crt": "-----BEGIN CERTIFICATE-----\nMIIGbDCCBVSgAwIBAgIQfpsSGBm0aOWQUqAGPoxrizANBgkqhkiG9w0BAQsFADCB\nkDELMAkGA1UEBhMCR0IxGzAZBgNVBAgTEkdyZWF0ZXIgTWFuY2hlc3RlcjEQMA4G\nA1UEBxMHU2FsZm9yZDEaMBgGA1UEChMRQ09NT0RPIENBIExpbWl0ZWQxNjA0BgNV\n...Many more lines that look like this...\ngInCCoyPSIRMKy1l84XmzgFV065g3kqxHCK8O0jpkFWgF2xbZBJCj0tWnNaWXPId\ndf6VNFF4+x1ub1x92UZ6ag==\n-----END CERTIFICATE-----",
  "domain_count": 2,
  "is_multi_domain": true,
  "is_wildcard": false,
  "is_installable": true,
  "is_expired": false,
  "alt_names": [
    "www.example.com",
    "example.com"
  ]
}

```

### Create a certificate

There are two variations to creating a certificate. In the first one a signing Certificate Signing Request and Private Key are supplied, in the other they are not. In the second scenario, the system will collect the needed information and generate the CSR and Key for the user.

In both scenarios, the type of certificate being purchased must be specified by giving the "package id" for the certificate type being purchased. For a complete list of values use the [Types of certificates that can be purchased](Packages.md#types-of-certificates-that-can-be-purchased) endpoint.

#### Creating a certificate from a CSR and Private Key

This is very similar to importing an existing certificate. The difference is that when creating a certificate, the certificate itself is omitted and the CSR is provided. Additionally two other parameters are provided, `months` and `package_id`.

__Parameters__

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
|`csr`| The certificate signing request | String | YES |
|`key`| The private key | String | YES |
|`months`| Number of months this certificate will be valid for. Must be a multiple of 12. | Integer | YES |
|`package_id`| The SSSL package to be purchased. See [Types of certificates that can be purchased](Packages.md#types-of-certificates-that-can-be-purchased) for a complete list.| Integer | YES |


__Example 5__
```shell
#!/bin/bash

CSR="-----BEGIN CERTIFICATE-----
MIIGbDCCBVSgAwIBAgIQfpsSGBm0aOWQUqAGPoxrizANBgkqhkiG9w0BAQsFADCB
         ...Many more lines that look like that...
gInCCoyPSIRMKy1l84XmzgFV065g3kqxHCK8O0jpkFWgF2xbZBJCj0tWnNaWXPId
df6VNFF4+x1ub1x92UZ6ag==
-----END CERTIFICATE-----"

KEY="-----BEGIN PRIVATE KEY-----
MIIJQwIBADANBgkqhkiG9w0BAQEFAASCCS0wggkpAgEAAoICAQCliHpsXji5TOQZ
        ...Many MANY more lines that look like that...
mWvRtmCdwO45XMKPLkglubG/PS/GEgXOscvT0mjExPAE+zHmnEShgN3Ph8ex2O2U
WS4xRl9VsWExMgBcPlqbUS/Uez+XTAw=
-----END PRIVATE KEY-----"

KEY=$(echo "$KEY" | php -r 'echo json_encode(file_get_contents("php://stdin"));' )
CSR=$(echo "$CSR" | php -r 'echo json_encode(file_get_contents("php://stdin"));' )

curl -v '__URL__/ssl-cert' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json' \
     --data-binary '{"csr": '"$CSR"', "key": '"$KEY"', "months", 12,"package_id": 179}'
```

#### Creating a certificate without a CSR and Private Key

When creating a certificate without a certificate Signing Request and private key, all of the information necessary to create the CSR must be passed into the request.

| Name | Description | Type | Required |
| :--- | :--- | :---: | :---: |
|`months`| Number of months this certificate will be valid for. Must be a multiple of 12. | Integer | YES |
|`package_id`| The SSSL package to be purchased. See [Types of certificates that can be purchased](Packages.md#types-of-certificates-that-can-be-purchased) for a complete list.| Integer | YES |
|`domain`| The fully qualified domain name (FQDN) that the certificate is for. | String | YES |
|`approver_email`| The key of the array must match `domain` above. The value **MUST** be "admin", "administrator","hostmaster", "postmaster","webmaster" at the domain specified in the certificate. If the domain specified is a subdomain, "admin or "administrator" at the root domain can also be used. (e.g. "admin@blog.example.com" or "administrator@example.com")  | Array | NO |
|`distinguished_name`| An array of the parts necessary to create the CSR. Contains the following seven items. | Array | YES |
|`email`| An email address used to contact the organization.| String | YES |
|`organization`| The legal name of the organization that owns the domain. Do not abbreviate and include any suffixes, such as Inc., Corp., or LLC. | String | YES |
|`street`| The street address for the owner of the domain  | String | YES |
|`locality`| The city where the organization is located. This shouldn’t be abbreviated.  | String | YES |
|`state`| TThe state/region where the organization is located. This shouldn't be abbreviated.  | String | YES |
|`country`| The two-letter code for the country where the organization is located.  | String | YES |
|`organizational_unit`| The division of the organization handling the certificate.  | String | NO |

```shell
curl -v '__URL__/ssl-cert' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json' \
     --data-binary '{ "months": "12", "package_id": "179", "domain": "example.com", "distinguished_name": { "email": "john@example.com", "street": "123 Main Street", "locality": "Anytown", "state": "MI", "country": "US", "organization": "Acme Examples", "organizational_unit": "marketing"}, "approver_email": {"example.com": "admin@example.com"}}'
```

The payload returned from both variations of the call are identical.

This payload has been truncated for brevity.

__Payload 5__

```json
{
  "order_id": XXXXX,
  "order_date": 1539004070,
  "package_id": 179,
  "client_id": XXXXX,
  "service_id": XXXXX
}
```

Creating a certificate is an out-of-bandwidth process. Therefore, these payloads do not contain the `ssl_cert_id`. The `service_id` can be used to query the  [Retrieve a certificate by `service_id`](#retrieve-a-certificate-by-service_id) endpoint. When the certificate is complete, the service will return a ssl-cert object as part of the payload. That will include the `ssl_cert_id` which can then be used on any of the `ssl-cert` endpoints.

## Delete

### Delete a certificate

Accessing the endpoint using the DELETE verb and providing a certificate_id as returned in GET or POST will remove the certificate from the system.

__Example 6__
```shell
curl -v -X DELETE '__URL__/ssl-cert/CERT_ID' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json'
```

When properly executed, the API endpoint will return a 200 OK but no payload.

