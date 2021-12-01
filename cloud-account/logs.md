# Portal: Cloud Account

## cloud-account:logs
Shows list of log files.

#### Access
cloud account view

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
      "#14 /home/nocworx/core/vendor/php-http/guzzle6-adapter/src/Client.php(56): Http\\Adapter\\Guzzle6\\Promise->wait()",
      "#15 /home/nocworx/core/vendor/lstrojny/fxmlrpc/src/fXmlRpc/Transport/HttpAdapterTransport.php(56): Http\\Adapter\\Guzzle6\\Client->sendRequest()",
      "#16 /home/nocworx/core/vendor/lstrojny/fxmlrpc/src/fXmlRpc/Client.php(154): fXmlRpc\\Transport\\HttpAdapterTransport->send()",
      "#17 /home/nocworx/core/vendor/nocworx/lib/src/NocWorx/Lib/Interworx/Client.php(164): fXmlRpc\\Client->call()",
      "#18 /home/nocworx/core/vendor/nocworx/lib/src/NocWorx/Lib/Interworx/ServerClient.php(340): NocWorx\\Lib\\Interworx\\Client->_send()",
      "#19 /home/nocworx/core/vendor/nocworx/lib/src/NocWorx/Lib/Interworx/ServerClient.php(996): NocWorx\\Lib\\Interworx\\ServerClient->_sendSiteworx()",
      "#20 /home/nocworx/core/src/NocWorx/Virt/Guest/CloudHost/Interworx.php(3402): NocWorx\\Lib\\Interworx\\ServerClient->getSiteworxSessionKey()",
      "#21 /home/nocworx/core/src/NocWorx/Virt/Guest/CloudAccount.php(4227): NocWorx\\Virt\\Guest\\CloudHost\\Interworx->getAccountLogFiles()",
      "#22 /home/nocworx/core/src/Api/Portal/V1/CloudAccount/Logs.php(62): NocWorx\\Virt\\Guest\\CloudAccount->getLogFiles()",
      "#23 /home/nocworx/core/src/Api/Handler/RequestHandler.php(165): NocWorx\\Api\\Portal\\V1\\CloudAccount\\Logs->_action()",
      "#24 /home/nocworx/core/src/Api/Handler/RequestHandler.php(135): NocWorx\\Api\\Handler\\RequestHandler->handle()",
      "#25 [internal function]: NocWorx\\Api\\Handler\\RequestHandler->__invoke()",
      "#26 /home/nocworx/core/vendor/slim/slim/Slim/Handlers/Strategies/RequestResponse.php(40): call_user_func()",
      "#27 /home/nocworx/core/vendor/slim/slim/Slim/Route.php(281): Slim\\Handlers\\Strategies\\RequestResponse->__invoke()",
      "#28 /home/nocworx/core/src/Api/Middleware/Middleware.php(94): Slim\\Route->__invoke()",
      "#29 /home/nocworx/core/src/Api/Middleware/Accept.php(70): class@anonymous->handle()",
      "#30 /home/nocworx/core/src/Api/Middleware/Middleware.php(99): NocWorx\\Api\\Middleware\\Accept->process()",
      "#31 [internal function]: NocWorx\\Api\\Middleware\\Middleware->__invoke()",
      "#32 /home/nocworx/core/vendor/slim/slim/Slim/DeferredCallable.php(57): call_user_func_array()",
      "#33 [internal function]: Slim\\DeferredCallable->__invoke()",
      "#34 /home/nocworx/core/vendor/slim/slim/Slim/MiddlewareAwareTrait.php(70): call_user_func()",
      "#35 /home/nocworx/core/src/Api/Middleware/Middleware.php(94): Slim\\Route->Slim\\{closure}()",
      "#36 /home/nocworx/core/src/Api/Middleware/CorsMiddleware.php(49): class@anonymous->handle()",
      "#37 /home/nocworx/core/src/Api/Middleware/Middleware.php(99): NocWorx\\Api\\Middleware\\CorsMiddleware->process()",
      "#38 [internal function]: NocWorx\\Api\\Middleware\\Middleware->__invoke()",
      "#39 /home/nocworx/core/vendor/slim/slim/Slim/DeferredCallable.php(57): call_user_func_array()",
      "#40 [internal function]: Slim\\DeferredCallable->__invoke()",
      "#41 /home/nocworx/core/vendor/slim/slim/Slim/MiddlewareAwareTrait.php(70): call_user_func()",
      "#42 /home/nocworx/core/src/Api/Middleware/Middleware.php(94): Slim\\Route->Slim\\{closure}()",
      "#43 /home/nocworx/core/src/Api/Middleware/InputParser.php(66): class@anonymous->handle()",
      "#44 /home/nocworx/core/src/Api/Middleware/Middleware.php(99): NocWorx\\Api\\Middleware\\InputParser->process()",
      "#45 [internal function]: NocWorx\\Api\\Middleware\\Middleware->__invoke()",
      "#46 /home/nocworx/core/vendor/slim/slim/Slim/DeferredCallable.php(57): call_user_func_array()",
      "#47 [internal function]: Slim\\DeferredCallable->__invoke()",
      "#48 /home/nocworx/core/vendor/slim/slim/Slim/MiddlewareAwareTrait.php(70): call_user_func()",
      "#49 /home/nocworx/core/src/Api/Middleware/Middleware.php(94): Slim\\Route->Slim\\{closure}()",
      "#50 /home/nocworx/core/src/Api/Portal/Middleware/Authorizer.php(75): class@anonymous->handle()",
      "#51 /home/nocworx/core/src/Api/Middleware/Middleware.php(99): NocWorx\\Api\\Portal\\Middleware\\Authorizer->process()",
      "#52 [internal function]: NocWorx\\Api\\Middleware\\Middleware->__invoke()",
      "#53 /home/nocworx/core/vendor/slim/slim/Slim/DeferredCallable.php(57): call_user_func_array()",
      "#54 [internal function]: Slim\\DeferredCallable->__invoke()",
      "#55 /home/nocworx/core/vendor/slim/slim/Slim/MiddlewareAwareTrait.php(70): call_user_func()",
      "#56 /home/nocworx/core/src/Api/Middleware/Middleware.php(94): Slim\\Route->Slim\\{closure}()",
      "#57 /home/nocworx/core/src/Api/Portal/Middleware/Authenticator.php(94): class@anonymous->handle()",
      "#58 /home/nocworx/core/src/Api/Middleware/Middleware.php(99): NocWorx\\Api\\Portal\\Middleware\\Authenticator->process()",
      "#59 [internal function]: NocWorx\\Api\\Middleware\\Middleware->__invoke()",
      "#60 /home/nocworx/core/vendor/slim/slim/Slim/DeferredCallable.php(57): call_user_func_array()",
      "#61 [internal function]: Slim\\DeferredCallable->__invoke()",
      "#62 /home/nocworx/core/vendor/slim/slim/Slim/MiddlewareAwareTrait.php(70): call_user_func()",
      "#63 /home/nocworx/core/vendor/slim/slim/Slim/MiddlewareAwareTrait.php(117): Slim\\Route->Slim\\{closure}()",
      "#64 /home/nocworx/core/vendor/slim/slim/Slim/Route.php(268): Slim\\Route->callMiddlewareStack()",
      "#65 /home/nocworx/core/vendor/slim/slim/Slim/App.php(503): Slim\\Route->run()",
      "#66 /home/nocworx/core/src/Api/Middleware/Middleware.php(94): Slim\\App->__invoke()",
      "#67 /home/nocworx/core/src/Api/Middleware/CorsMiddleware.php(49): class@anonymous->handle()",
      "#68 /home/nocworx/core/src/Api/Middleware/Middleware.php(99): NocWorx\\Api\\Middleware\\CorsMiddleware->process()",
      "#69 [internal function]: NocWorx\\Api\\Middleware\\Middleware->__invoke()",
      "#70 /home/nocworx/core/vendor/slim/slim/Slim/DeferredCallable.php(57): call_user_func_array()",
      "#71 [internal function]: Slim\\DeferredCallable->__invoke()",
      "#72 /home/nocworx/core/vendor/slim/slim/Slim/MiddlewareAwareTrait.php(70): call_user_func()",
      "#73 /home/nocworx/core/src/Api/Middleware/Middleware.php(94): Slim\\App->Slim\\{closure}()",
      "#74 /home/nocworx/core/src/Api/Middleware/AcceptFromExtension.php(57): class@anonymous->handle()",
      "#75 /home/nocworx/core/src/Api/Middleware/Middleware.php(99): NocWorx\\Api\\Middleware\\AcceptFromExtension->process()",
      "#76 [internal function]: NocWorx\\Api\\Middleware\\Middleware->__invoke()",
      "#77 /home/nocworx/core/vendor/slim/slim/Slim/DeferredCallable.php(57): call_user_func_array()",
      "#78 [internal function]: Slim\\DeferredCallable->__invoke()",
      "#79 /home/nocworx/core/vendor/slim/slim/Slim/MiddlewareAwareTrait.php(70): call_user_func()",
      "#80 /home/nocworx/core/src/Api/Middleware/Middleware.php(94): Slim\\App->Slim\\{closure}()",
      "#81 /home/nocworx/core/src/Api/Middleware/ApiInfo.php(48): class@anonymous->handle()",
      "#82 /home/nocworx/core/src/Api/Middleware/Middleware.php(99): NocWorx\\Api\\Middleware\\ApiInfo->process()",
      "#83 [internal function]: NocWorx\\Api\\Middleware\\Middleware->__invoke()",
      "#84 /home/nocworx/core/vendor/slim/slim/Slim/DeferredCallable.php(57): call_user_func_array()",
      "#85 [internal function]: Slim\\DeferredCallable->__invoke()",
      "#86 /home/nocworx/core/vendor/slim/slim/Slim/MiddlewareAwareTrait.php(70): call_user_func()",
      "#87 /home/nocworx/core/src/Api/Middleware/Middleware.php(94): Slim\\App->Slim\\{closure}()",
      "#88 /home/nocworx/core/src/Api/Middleware/RateLimiter.php(46): class@anonymous->handle()",
      "#89 /home/nocworx/core/src/Api/Middleware/Middleware.php(99): NocWorx\\Api\\Middleware\\RateLimiter->process()",
      "#90 [internal function]: NocWorx\\Api\\Middleware\\Middleware->__invoke()",
      "#91 /home/nocworx/core/vendor/slim/slim/Slim/DeferredCallable.php(57): call_user_func_array()",
      "#92 [internal function]: Slim\\DeferredCallable->__invoke()",
      "#93 /home/nocworx/core/vendor/slim/slim/Slim/MiddlewareAwareTrait.php(70): call_user_func()",
      "#94 /home/nocworx/core/vendor/slim/slim/Slim/MiddlewareAwareTrait.php(117): Slim\\App->Slim\\{closure}()",
      "#95 /home/nocworx/core/vendor/slim/slim/Slim/App.php(392): Slim\\App->callMiddlewareStack()",
      "#96 /home/nocworx/core/vendor/slim/slim/Slim/App.php(297): Slim\\App->process()",
      "#97 /home/nocworx/core/src/Api/Api.php(259): Slim\\App->run()",
      "#98 /home/nocworx/core/public/api/portal.php(8): NocWorx\\Api\\Api->run()",
      "#99 {main}"
    ]
  },
  
  . . .
]
```

**Failure Response** (not logged in, expired token, etc.): 401 Unauthorized

**Failure Response** (insufficient permissions): 403 Forbidden
