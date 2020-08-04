Admin: Api Tasks
----------------

**since** 0.5.0

api-task:show
=============

Shows details of an Api Task.

The admin endpoint differs from portal:api-task:show in that it includes internal (i.e., 5xx class) error messages and stack traces in addition to client-facing errors.

**Endpoint**:  GET /v1/task/{uuid}

**Access**: api_task view permission; all users can view their own api tasks

**Parameters**: none

**Request**:
```
curl -i "$NW_API/v1/task/$TASK_UUID" \
  -H "Authorization: Bearer $NW_KEY" \
  -H "Accept: application/json"
```

**Success Response**: 200 OK
```
HTTP/1.1 200 OK
Server: nginx
Date: Tue, 04 Aug 2020 03:07:01 GMT
Content-Type: application/json
Content-Length: 3249
Keep-Alive: timeout=5
Vary: Accept-Encoding
X-Powered-By: PHP/7.4.2
NocWorx-Api-Version: 0.5.0
Served-By: nwdev-web01-int

{
  "id": 730,
  "identity": "cloud-server:add-cluster (failure)",
  "status": "failure",
  "action": "cloud-server:add-cluster",
  "api_version": "0.5.0",
  "errors": {
    "message": "The task could not be completed. If this problem persists, please contact support and provide the task uuid."
  },
  "input": {
    "fiat": "environment: ...",
    "use_password": true,
    "cloud_id": 1,
    "ssh_key_ids": null,
    "addon_ids": null,
    "discount_code": null,
    "package_id": 769
  },
  "internal_errors": [
    {
      "message": "NocWorx_Virt_Exception ##LG_NO_AVAILABILITY_ZONES##: us-midwest-1 - n5s-gp-1.tiny[virtual]",
      "trace": [
        {
          ...
      ]
    }
  ],
  "metadata": {
    "scope": "api-task",
    "uri": "/v1/task/123e4567-e89b-12d3-a456-426614174000/"
  },
  "request_date": 1596485303,
  "resolved_date": 1596485289,
  "resource": {
    "id": 40672,
    "identity": "(40672) Bosco-Bradtke",
    "metadata": {
      "scope": "order",
      "uri": null
    }
  },
  "staff_user": {
    "id": 123,
    "identity": "NocWorx Admin",
    "metadata": {
      "scope": "agent",
      "uri": null
    }
  },
  "user": {
    "id": 27767,
    "identity": "Annabel Whyman - user@nocworx.com",
    "metadata": {
      "scope": "user",
      "uri": null
    }
  },
  "uuid": "123e4567-e89b-12d3-a456-426614174000"
}
```

**Failure Response** (not logged in): 401 Unauthorized

**Failure Response** (doesn't exist / not visible): 404 Not Found
