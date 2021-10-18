# Portal: Address

## address:add
Creates a new Address.

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
logged-in users

#### Input
- string `address1` (required): address1; must contain a single line of printable characters only
- string `address2` (optional): address2; Value must contain a single line of printable characters only
- string `city` (required): city; must contain a single line of printable characters only
- string `state` (required): state; one of OT|AL|AK|AB|AZ|AR|BC|CA|CO|CT|DE|DC|FL|GA|HI|ID|IL|IN|IA|KS|KY|LA|ME|MB|MD|MA|MI|MN|MS|MO|MT|NE|NV|NL|NB|NH|NJ|NM|NY|NT|NC|ND|NS|NU|OH|OK|ON|OR|PA|PE|QC|RI|SK|SC|SD|TN|TX|UT|VT|VA|WA|WV|WI|WY|YT
- string `country` (required): country; one of TW|AF|AL|DZ|AS|AD|AO|AI|AQ|AG|AR|AM|AW|AU|AT|AZ|BS|BH|BD|BB|BY|BE|BZ|BJ|BM|BT|BO|BQ|BA|BW|BV|BR|IO|VG|BN|BG|BF|BI|CV|KH|CM|CA|KY|CF|TD|CL|CN|HK|MO|CX|CC|CO|KM|CG|CK|CR|HR|CU|CW|CY|CZ|CI|KP|CD|DK|DJ|DM|DO|EC|EG|SV|GQ|ER|EE|SZ|ET|FK|FO|FJ|FI|FR|GF|PF|TF|GA|GM|GE|DE|GH|GI|GR|GL|GD|GP|GU|GT|GG|GN|GW|GY|HT|HM|VA|HN|HU|IS|IN|ID|IR|IQ|IE|IM|IL|IT|JM|JP|JE|JO|KZ|KE|KI|KW|KG|LA|LV|LB|LS|LR|LY|LI|LT|LU|MG|MW|MY|MV|ML|MT|MH|MQ|MR|MU|YT|MX|FM|MC|MN|ME|MS|MA|MZ|MM|NA|NR|NP|NL|NC|NZ|NI|NE|NG|NU|NF|MP|NO|OM|PK|PW|PA|PG|PY|PE|PH|PN|PL|PT|PR|QA|KR|MD|RO|RU|RW|RE|BL|SH|KN|LC|MF|PM|VC|WS|SM|ST|XX|SA|SN|RS|SC|SL|SG|SX|SK|SI|SB|SO|ZA|GS|SS|ES|LK|PS|SD|SR|SJ|SE|CH|SY|TJ|TH|MK|TL|TG|TK|TO|TT|TN|TR|TM|TC|TV|UG|UA|AE|GB|TZ|UM|VI|US|UY|UZ|VU|VE|VN|WF|EH|YE|ZM|ZW|AX
- string `zip` (required): zip; must contain a single line of printable characters only
- string `type` (optional): type; one of affiliate|billing|technical|rwhois|abuse|other
- string `company` (optional): company; must contain a single line of printable characters only
- string `first_name` (required): first_name; must contain a single line of printable characters only
- string `last_name` (required): last_name; must contain a single line of printable characters only
- string `email` (required): Invalid e-mail
- string `phone` (optional): phone; must contain a single line of printable characters only
- string `cell` (optional): cell; must contain a single line of printable characters only
- string `fax` (optional): fax; must contain a single line of printable characters only

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/address" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{"address1":"21700 Melrose Ave","address2":"21700 Melrose Ave","country":"US","state":"MI","zip":"48075","type":"billing","city":"Southfield","first_name":"first name","last_name":"last name","email":"nocworx-dev@nexcess.net"}'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Mon, 18 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
X-Powered-By: PHP/7.2.15
Location: /v1/address
NocWorx-Api-Version: 0.0.0
Served-By: nwdev-web01-int

{ "id": 12345, "identity": "address:add (pending)" }"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
