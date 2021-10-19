# Portal: Address

## address:edit
Edits a stored Address

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will describe the requested task, and will also include a Location header that can be polled to determine the status of the task. @see task:show.

#### Access
logged-in users

#### Input
- integer `id` (required): id; must be integer
- string `address1` (optional): address1; must contain a single line of text
- string `address2` (optional): address2; must contain a single line of text
- string `city` (optional): city; must contain a single line of text
- string `state` (optional): state; one of OT|AL|AK|AB|AZ|AR|BC|CA|CO|CT|DE|DC|FL|GA|HI|ID|IL|IN|IA|KS|KY|LA|ME|MB|MD|MA|MI|MN|MS|MO|MT|NE|NV|NL|NB|NH|NJ|NM|NY|NT|NC|ND|NS|NU|OH|OK|ON|OR|PA|PE|QC|RI|SK|SC|SD|TN|TX|UT|VT|VA|WA|WV|WI|WY|YT
- string `country` (optional): country; one of TW|AF|AL|DZ|AS|AD|AO|AI|AQ|AG|AR|AM|AW|AU|AT|AZ|BS|BH|BD|BB|BY|BE|BZ|BJ|BM|BT|BO|BQ|BA|BW|BV|BR|IO|VG|BN|BG|BF|BI|CV|KH|CM|CA|KY|CF|TD|CL|CN|HK|MO|CX|CC|CO|KM|CG|CK|CR|HR|CU|CW|CY|CZ|CI|KP|CD|DK|DJ|DM|DO|EC|EG|SV|GQ|ER|EE|SZ|ET|FK|FO|FJ|FI|FR|GF|PF|TF|GA|GM|GE|DE|GH|GI|GR|GL|GD|GP|GU|GT|GG|GN|GW|GY|HT|HM|VA|HN|HU|IS|IN|ID|IR|IQ|IE|IM|IL|IT|JM|JP|JE|JO|KZ|KE|KI|KW|KG|LA|LV|LB|LS|LR|LY|LI|LT|LU|MG|MW|MY|MV|ML|MT|MH|MQ|MR|MU|YT|MX|FM|MC|MN|ME|MS|MA|MZ|MM|NA|NR|NP|NL|NC|NZ|NI|NE|NG|NU|NF|MP|NO|OM|PK|PW|PA|PG|PY|PE|PH|PN|PL|PT|PR|QA|KR|MD|RO|RU|RW|RE|BL|SH|KN|LC|MF|PM|VC|WS|SM|ST|XX|SA|SN|RS|SC|SL|SG|SX|SK|SI|SB|SO|ZA|GS|SS|ES|LK|PS|SD|SR|SJ|SE|CH|SY|TJ|TH|MK|TL|TG|TK|TO|TT|TN|TR|TM|TC|TV|UG|UA|AE|GB|TZ|UM|VI|US|UY|UZ|VU|VE|VN|WF|EH|YE|ZM|ZW|AX
- string `zip` (optional): zip; must contain a single line of E_164 format preferred
- string `type` (optional): type; one of affiliate|billing|technical|rwhois|abuse|other
- string `company` (optional): company name; must contain a single line of text
- string `first_name` (optional): addressee's first name; must contain a single line of text
- string `last_name` (optional): addressee's last_name; must contain a single line of text
- string `email` (optional): a valid, verifiable email address
- string `phone` (optional): phone number; must contain a single line of E_164 format preferred
- string `cell` (optional): cell number; must contain a single line of E_164 format preferred
- string `fax` (optional): fax number; must contain a single line of E_164 format preferred

#### Request
```
$ curl -i -X POST "$PORTAL_API_URL/v1/address/{id}" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "id":"1234",
    "address1":"21700 Melrose Ave",
    "country":"US",
    "state":"MI",
    "zip":"48075",
    "type":"billing",
    "city":"Southfield",
    "first_name":"William",
    "last_name":"Louis",
    "email":"support@nexcess.net"
  }'
```

#### Responses
**Success Response** (request was accepted for processing): 202 Accepted
```
HTTP/1.1 202 Accepted
Date: Mon, 19 Oct 2021 12:51:27 GMT
Content-Type: application/json;charset=utf-8
Content-Length: 44
Location: /v1/address/1234
NocWorx-Api-Version: 0.0.0

{ "id": 1234, "identity": "address:edit (pending)" }"
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
