# SSL-Cert

**End Point**

```
/ssl-cert
```
The `/ssl-cert` endpoint allows you to Install, retrieve and remove SSL certificates attached to the account holding the API key.

**Accepted Verbs**

- GET
  - [List all Certificates](#list-all-certificates)
  - [Retrieve a Certificate](#retrieve-a-certificate)
- POST
  - [Import Certificate](#import-certificate)
- Delete
  - [Delete Certificate](#delete-certificate)

## GET

### List all Certificates

To retrieve all the information about all the certificates associated with an account, GET the `ssl-cert` endpoint without specifying a specific CERT_ID.

__Example 1__
```shell
curl -v 'https://demo2.nocworx.com/extranet/ssl-cert' \
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
      "description": "SSL Certificate - RVRepair.Directory",
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

### Retrieve a Certificate

The API can return the data for a single certificate as well as [List all Certificates](#list-all-certificates). To retrieve a single certificate, append the `cert_id` to the end of the URL.

__Example 2__
```shell
curl -v 'https://demo2.nocworx.com/extranet/ssl-cert/CERT_ID' \
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

## POST

### Import Certificate
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

__Example 3__
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

curl -v 'https://demo2.nocworx.com/extranet/ssl-cert' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json' \
     --data-binary '{"chain_cert": '"$CHAIN"', "crt": '"$CRT"', "key": '"$KEY"'}'
```

When properly encoded valid data is transmitted to the endpoint, the return payload will contain the newly created SSL certificate record ready to be attached to a cloud account.

__Payload 3__
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

## Delete

### Delete Certificate

Accessing the endpoint using the DELETE verb and providing a certificate_id as returned in GET or POST will remove the certificate from the system.

__Example 4__
```shell
curl -v 'https://demo2.nocworx.com/extranet/ssl-cert/CERT_ID' \
     -H 'Authorization: Bearer YOUR_VERY_LONG_API_KEY_GOES_HERE' \
     -H 'Content-Type: application/json' \
     -H 'Accept: application/json'
```

When properly executed, the API endpoint will return a 200 OK but no payload.

