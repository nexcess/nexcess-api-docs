# Portal: Cloud Account

## cloud-account:logs
Shows list of log files.

#### Access
service view

#### Request
```
$ curl "$PORTAL_API_URL/v1/cloud-account/{id}/log" \
  -H "Authorization: Bearer $PORTAL_API_KEY" \
  -H "Accept: application/json" 
```

#### Responses
**Success Response** (Error): 500 Internal Server Error
```
HTTP/1.1 500 Internal Server Error
Date: Wed, 24 Nov 2021 12:51:27 GMT
Content-Length: 44
Location: /v1/cloud-account/12345/log
NocWorx-Api-Version: 0.0.0

[
  {
    "log_file": "/chroot/home/a9c1c849/var/e8fbc88859.400.lwdns.dev/logs/error-2022-01-07.log",
    "date": 1641549132,
    "download_url": "https://192.190.222.114:2443/siteworx/index?action=sso&sid=1l13r7m2p3q7cdms48jhb0si6q&uri=L3NpdGV3b3J4L2Rvd25sb2FkP2FjdGlvbj1sb2cmZmlsZT0lMkZjaHJvb3QlMkZob21lJTJGYTljMWM4NDklMkZ2YXIlMkZlOGZiYzg4ODU5LjQwMC5sd2Rucy5kZXYlMkZsb2dzJTJGZXJyb3ItMjAyMi0wMS0wNy5sb2cmZG9tYWluPWU4ZmJjODg4NTkuNDAwLmx3ZG5zLmRldg%3D%3D"
  },
  
  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
