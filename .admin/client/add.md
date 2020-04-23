Admin: Client
-------------

**since** 0.2.0

client:add
==========

Creates a new Client account and its initial Client User (owner).

This task is queued, meaning it will be completed out-of-band from the current request. The response payload will include a Location header that can be polled to determine the status of the task. @see task:show.

**Endpoint**: POST /v1/client

**Parameters**:

_…for "company use" companies_

New clients for "Company Use" Companies will be assigned that company's "blackhole" user automatically. No user information should be provided (it will be ignored). Note that `company_use` _must_ be provided, and must be `true`, for any client created for a company-use company.

New "company use" clients may be created for non-company-use companies as well; the above note does not apply to this case.

_…for all cases_
- integer `company_id` (required): Serial id of the Company to add the new Client under
- boolean `company_use` (required if company is company use only): Is the client for company use?
- string `external_key` (optional): Arbitrary client identifier
- string `name` (required): A name for the Client account
- int `account_manager_id` (optional): Id of the agent (staff user) that will manage this account

_…when assigning an existing client user as account owner_
- int `user_id` (required): Id of an existing user to assign as the owner of this account

No other user information should be provided (it will be ignored).

_…when creating a new client user as account owner_
- string `email` (required): User's email address
- string `first_name` (required): User's first name
- string `last_name` (required): User's last name

_…when including a default address for the client_
- string `company` (optional): Company name (as should be displayed with this address)
- string `address1` (required): Street address (line 1)
- string `address2` (optional): Street address (line 2)
- string `city` (required): City or town
- string `state` (required): State or province; one of `OT`("other")|`AL`|`AK`|`AB`|`AZ`|`AR`|`BC`|`CA`|`CO`|`CT`|`DE`|`DC`|`FL`|`GA`|`HI`|`ID`|`IL`|`IN`|`IA`|`KS`|`KY`|`LA`|`ME`|`MB`|`MD`|`MA`|`MI`|`MN`|`MS`|`MO`|`MT`|`NE`|`NV`|`NL`|`NB`|`NH`|`NJ`|`NM`|`NY`|`NT`|`NC`|`ND`|`NS`|`NU`|`OH`|`OK`|`ON`|`OR`|`PA`|`PE`|`QC`|`RI`|`SK`|`SC`|`SD`|`TN`|`TX`|`UT`|`VT`|`VA`|`WA`|`WV`|`WI`|`WY`|`YT`
- string `country` (required): Country; one of `TW`|`AF`|`AL`|`DZ`|`AS`|`AD`|`AO`|`AI`|`AQ`|`AG`|`AR`|`AM`|`AW`|`AU`|`AT`|`AZ`|`BS`|`BH`|`BD`|`BB`|`BY`|`BE`|`BZ`|`BJ`|`BM`|`BT`|`BO`|`BQ`|`BA`|`BW`|`BV`|`BR`|`IO`|`VG`|`BN`|`BG`|`BF`|`BI`|`CV`|`KH`|`CM`|`CA`|`KY`|`CF`|`TD`|`CL`|`CN`|`HK`|`MO`|`CX`|`CC`|`CO`|`KM`|`CG`|`CK`|`CR`|`HR`|`CU`|`CW`|`CY`|`CZ`|`CI`|`KP`|`CD`|`DK`|`DJ`|`DM`|`DO`|`EC`|`EG`|`SV`|`GQ`|`ER`|`EE`|`ET`|`FK`|`FO`|`FJ`|`FI`|`FR`|`GF`|`PF`|`TF`|`GA`|`GM`|`GE`|`DE`|`GH`|`GI`|`GR`|`GL`|`GD`|`GP`|`GU`|`GT`|`GG`|`GN`|`GW`|`GY`|`HT`|`HM`|`VA`|`HN`|`HU`|`IS`|`IN`|`ID`|`IR`|`IQ`|`IE`|`IM`|`IL`|`IT`|`JM`|`JP`|`JE`|`JO`|`KZ`|`KE`|`KI`|`KW`|`KG`|`LA`|`LV`|`LB`|`LS`|`LR`|`LY`|`LI`|`LT`|`LU`|`MG`|`MW`|`MY`|`MV`|`ML`|`MT`|`MH`|`MQ`|`MR`|`MU`|`YT`|`MX`|`FM`|`MC`|`MN`|`ME`|`MS`|`MA`|`MZ`|`MM`|`NA`|`NR`|`NP`|`NL`|`NC`|`NZ`|`NI`|`NE`|`NG`|`NU`|`NF`|`MP`|`NO`|`OM`|`PK`|`PW`|`PA`|`PG`|`PY`|`PE`|`PH`|`PN`|`PL`|`PT`|`PR`|`QA`|`KR`|`MD`|`RO`|`RU`|`RW`|`RE`|`BL`|`SH`|`KN`|`LC`|`MF`|`PM`|`VC`|`WS`|`SM`|`ST`|`XX`|`SA`|`SN`|`RS`|`SC`|`SL`|`SG`|`SX`|`SK`|`SI`|`SB`|`SO`|`ZA`|`GS`|`SS`|`ES`|`LK`|`PS`|`SD`|`SR`|`SJ`|`SZ`|`SE`|`CH`|`SY`|`TJ`|`TH`|`MK`|`TL`|`TG`|`TK`|`TO`|`TT`|`TN`|`TR`|`TM`|`TC`|`TV`|`UG`|`UA`|`AE`|`GB`|`TZ`|`UM`|`VI`|`US`|`UY`|`UZ`|`VU`|`VE`|`VN`|`WF`|`EH`|`YE`|`ZM`|`ZW`|`AX`
- string `zip` (required): Zip code / postal code
- string `phone` (required): Phone number (formatting is permitted but ignored)
- string `cell` (optional): Cellular phone number (formatting is permitted but ignored)
- string `fax` (optional): Fax number (formatting is permitted but ignored)

**Request**:
```
curl -i -X POST "$ADMIN_API_URL/v1/client" \
  -H "Authorization: Bearer $ADMIN_API_KEY" \
  -H "Content-type: application/json" \
  -H "Accept: application/json" \
  -d '{
    "company_id": "'"$COMPANY_ID"'",
    "company_use": true,
    "external_key": "'"$EXTERNAL_CUSTOMER_ID"'",
    "name": "Bob Coleman"
  }'
```

**Success Response**:
```
HTTP/1.1 202 Accepted
Server: nginx
Date: Thu, 19 Sep 2019 20:11:20 GMT
Content-Type: application/json
Content-Length: 245
Keep-Alive: timeout=5
X-Powered-By: PHP/7.2.21
Location: /v1/task/48d96192-8108-470b-9b4f-9275c312055e
NocWorx-Api-Version: 0.1.0
Served-By: nwdev-web01-int

{
  "id":134,
  "identity":"client:add (pending)",
  "status":"pending",
  "action":"client:add",
  "request_date":1568923879,
  "resource":null,
  "staff_user":{
    "id":1,
    "identity":"NocWorx Admin",
    "uri":null
  },
  "user":null,
  "uuid":"48d96192-8108-470b-9b4f-9275c312055e"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (invalid inputs): 422 Unprocessable Entity
