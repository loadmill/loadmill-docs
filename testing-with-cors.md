# Testing With CORS

Loadmill uses real browser sessions to test your application/web server. This means you must allow CORS in your server code.

The following example code shows exactly how do it for an [Express.js](http://expressjs.com/) application - feel free to copy & paste ;\)

```js
var app = require("express")();

// ...

app.use(function (req, res, next) {
    const origin = req.header("Origin");
    const requestMethod = req.header("Access-Control-Request-Method");

    if (origin === "http://www.loadmill.com"
        || origin === "https://www.loadmill.com") {

        res.header("Access-Control-Allow-Origin", origin);

        if (req.method === 'OPTIONS' && origin && requestMethod) {
            // It's a pre-flight request:
            const requestHeaders = req.header("Access-Control-Request-Headers");
            setPreFlightHeaders(res, requestMethod || "", requestHeaders || "");

            return res.sendStatus(204);
        }
        else {
            const exposedHeaders = req.header("Loadmill-Request-Expose-Headers") || "";
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



