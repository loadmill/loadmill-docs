# Testing with CORS

Loadmill uses real browser sessions to test your application/web server. This means you must allow [CORS](https://en.wikipedia.org/wiki/Cross-origin_resource_sharing\) in your server code \(just for us - no third parties need to be allowed\).

[Enabling CORS](https://enable-cors.org/server.html) mainly involves reading request headers and writing reponse headers accordingly on your server. The following example code shows exactly how to enable CORS for [Loadmill](https://www.loadmill.com) tests in your [Express.js](http://expressjs.com/) application - feel free to copy & paste ;\)

If you are not sure how to enable CORS in your application or would like to see examples for different languages/frameworks, please contact us at [support@loadmill.com](mailto:support@loadmill.com).

```js
var app = require("express")();

// This part goes before your own handlers:
app.use(function (req, res, next) {
    var origin = req.header("Origin");
    var requestMethod = req.header("Access-Control-Request-Method");

    if (origin === "http://www.loadmill.com"
        || origin === "https://www.loadmill.com") {

        res.header("Access-Control-Allow-Origin", origin);

        if (req.method === 'OPTIONS' && origin && requestMethod) {
            // It's a pre-flight request:
            var requestHeaders = req.header("Access-Control-Request-Headers");
            setPreFlightHeaders(res, requestMethod || "", requestHeaders || "");

            return res.sendStatus(204);
        }
        else {
            var exposedHeaders = req.header("Loadmill-Request-Expose-Headers") || "";
            res.header("Access-Control-Expose-Headers", exposedHeaders);
        }
    }
    return next();
});

function setPreFlightHeaders(res, allowedMethod, allowedHeaders) {
    res.header({
        // 24h: maximum in Firefox, 5m for other browsers
        "Access-Control-Max-Age": "86400",
        "Access-Control-Allow-Methods": allowedMethod,
        "Access-Control-Allow-Headers": allowedHeaders
    });
}
```



