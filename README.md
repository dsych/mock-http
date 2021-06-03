# mock-server.js
A simple zero-config server for mocking HTTP(S) urls for quick testing.

# Features
* Simulate response from a single url with headers, body, response code etc.
* Support for HTTP and HTTPS

# What it does
Run it with `npx` and supply `url`, `method` and `response code` for the mock response. Watch it run and in a different terminal query the url.
Here is a taste:
> terminal 1:
```bash
$ npx mock-server -m POST -u /my-route -s 200 --header content-type:application/json -b '{"status":"Success"}'
Starting insecure server on port 8000
Serving /my-route with method POST
```
> terminal 2:
```bash
$ curl -X POST localhost:8000/my-route -v

*   Trying 127.0.0.1...
* TCP_NODELAY set
* Connected to localhost (127.0.0.1) port 8000 (#0)
> POST /my-route HTTP/1.1
> Host: localhost:8000
> User-Agent: curl/7.58.0
> Accept: */*
>
< HTTP/1.1 200 OK
< content-type: application/json
< content-length: 18
< Date: Thu, 03 Jun 2021 21:34:02 GMT
< Connection: keep-alive
< Keep-Alive: timeout=5
<
* Connection #0 to host localhost left intact
"{status":"Success}"
```

> NOTE: of course this also works with other HTTP clients like browsers, HTTP services etc.

# How it works
Just supply 3 things on the command line through options:
1. Url to be server
2. HTTP method to listen to. This could also be `*` in order to listen for any method
3. Response code to be returned

There are additional things that could be set like `body` and `headers`, but they are optional.
> For full details run with `-h`.

# Credits
This work is fully based on [mock-http-server](https://www.npmjs.com/package/mock-http-server), so all the credit goes to it :)
If you have a more complicated use case like returning different response bodies based on parameters etc. I recommend checking `mock-http-server` out!
It provides a programmatic interface for filtering, hooks etc.
