# Testing with CORS

## Testing with CORS

For high volume load tests, [Loadmill](https://www.loadmill.com) uses real browser sessions to test your application/web server. This requires that you allow [CORS](https://en.wikipedia.org/wiki/Cross-origin\_resource\_sharing) in your server code (just for us - no third parties need to be allowed).

[Enabling CORS](https://enable-cors.org/server.html) mainly involves reading request headers and writing response headers accordingly on your server. The following example code shows exactly how to enable CORS for Loadmill tests in an [express.js](http://expressjs.com) application.

Express users **don't need to copy this example**, simply use our npm module: [express-loadmill](https://www.npmjs.com/package/express-loadmill)

```javascript
var app = require("express")();

// Handle CORS before processing requests:
app.use(function (req, res, next) {
    // This request header contains the host of the CORS client:
    var origin = req.header("Origin");

    // This request header contains the HTTP request method: 
    var requestMethod = req.header("Access-Control-Request-Method");

    if (origin === "http://www.loadmill.com"
        || origin === "https://www.loadmill.com") {

        // This response header allows CORS from loadmill.com:
        res.header("Access-Control-Allow-Origin", origin);

        // This response header is required only if you use cookies in your tests:
        res.header("Access-Control-Allow-Credentials", 'true');

        if (req.method === 'OPTIONS' && origin && requestMethod) {
            // It's a pre-flight request:

            // This request header contains the request headers of the pre-flighted request:
            var requestHeaders = req.header("Access-Control-Request-Headers");

            setPreFlightHeaders(res, requestMethod || "", requestHeaders || "");
            return res.sendStatus(204);
        }
        else {
            // If your test scenario involves reading response headers, 
            // we automatically include them in this request header:
            var exposedHeaders = req.header("Loadmill-Request-Expose-Headers") || "";

            // This response header allows the test client to read the desired headers from the response:
            res.header("Access-Control-Expose-Headers", exposedHeaders);
        }
    }
    return next();
});

function setPreFlightHeaders(res, allowedMethod, allowedHeaders) {
    res.header({
        // This response header asks the browser not to pre-flight 
        // the same request URL again for the next 24 hours:
        "Access-Control-Max-Age": "86400",

        // These response headers approve the request method and headers specified:
        "Access-Control-Allow-Methods": allowedMethod,
        "Access-Control-Allow-Headers": allowedHeaders
    });
}
```

If you are not sure how to enable CORS in your application or would like to see examples for different languages/frameworks, please contact us at [support@loadmill.com](mailto:support@loadmill.com).

## Express Middleware

If you _are_ using [node.js](https://nodejs.org) and [express](https://expressjs.com) you can simply use our npm module: [express-loadmill](https://www.npmjs.com/package/express-loadmill).

It may also be used for quick and easy [domain verification](../load-testing/domain-verification.md).
