# SSL-Cert

**End Point**

```
/ssl-cert
```
The `/service` endpoint allows you to query and modify some of the attributes of a given service. When you create a cloud-account, a service is also created and associated with that cloud account. The service represents the actual server and application installed and contains all the technical parameters that can be see or modified.

**Accepted Verbs**

- GET
  - [Import Certificate](#import-certificate)
- POST
- Delete

## GET


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

When properly encoded valid data is transmitted to the endpoint, the return payload will contain the newly created ssl certificate record ready to be attached to a cloud account.

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