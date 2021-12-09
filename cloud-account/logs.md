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
    "type": "GuzzleHttp\\Exception\\ConnectException",
    "code": 0,
    "message": "cURL error 7: Failed connect to 192.190.222.73:2443; Connection timed out (see https://curl.haxx.se/libcurl/c/libcurl-errors.html)",
    "file": "/home/nocworx/core/vendor/guzzlehttp/guzzle/src/Handler/CurlFactory.php",
    "line": 200,
    "trace": [
      "#0 /home/nocworx/core/vendor/guzzlehttp/guzzle/src/Handler/CurlFactory.php(155): GuzzleHttp\\Handler\\CurlFactory::createRejection()",
      "#1 /home/nocworx/core/vendor/guzzlehttp/guzzle/src/Handler/CurlFactory.php(105): GuzzleHttp\\Handler\\CurlFactory::finishError()",
      "#2 /home/nocworx/core/vendor/guzzlehttp/guzzle/src/Handler/CurlHandler.php(43): GuzzleHttp\\Handler\\CurlFactory::finish()",
      "#3 /home/nocworx/core/vendor/guzzlehttp/guzzle/src/RetryMiddleware.php(70): GuzzleHttp\\Handler\\CurlHandler->__invoke()",
      "#4 /home/nocworx/core/vendor/guzzlehttp/guzzle/src/RetryMiddleware.php(126): GuzzleHttp\\RetryMiddleware->__invoke()",
      "#5 /home/nocworx/core/vendor/guzzlehttp/guzzle/src/RetryMiddleware.php(115): GuzzleHttp\\RetryMiddleware->doRetry()",
      "#6 /home/nocworx/core/vendor/guzzlehttp/promises/src/RejectedPromise.php(42): GuzzleHttp\\RetryMiddleware->GuzzleHttp\\{closure}()",
      "#7 /home/nocworx/core/vendor/guzzlehttp/promises/src/TaskQueue.php(48): GuzzleHttp\\Promise\\RejectedPromise::GuzzleHttp\\Promise\\{closure}()",
      "#8 /home/nocworx/core/vendor/guzzlehttp/promises/src/Promise.php(248): GuzzleHttp\\Promise\\TaskQueue->run()",
      "#9 /home/nocworx/core/vendor/guzzlehttp/promises/src/Promise.php(224): GuzzleHttp\\Promise\\Promise->invokeWaitFn()",
      "#10 /home/nocworx/core/vendor/guzzlehttp/promises/src/Promise.php(269): GuzzleHttp\\Promise\\Promise->waitIfPending()",
      "#11 /home/nocworx/core/vendor/guzzlehttp/promises/src/Promise.php(226): GuzzleHttp\\Promise\\Promise->invokeWaitList()",
      "#12 /home/nocworx/core/vendor/guzzlehttp/promises/src/Promise.php(62): GuzzleHttp\\Promise\\Promise->waitIfPending()",
      "#13 /home/nocworx/core/vendor/php-http/guzzle6-adapter/src/Promise.php(95): GuzzleHttp\\Promise\\Promise->wait()",
      "#14 /home/nocworx/core/vendor/php-http/guzzle6-adapter/src/Client.php . . .
    ]
  },
  
  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden

**Failure Response** (id doesn't exist on your account (or at all)): 404 Not Found
