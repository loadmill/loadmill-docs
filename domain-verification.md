# Domain Verification

**Domain verification** is the process of verifying that your domain actually belongs to you, so we can load-test it.

For example, if you have an app hosted on `myapp.com` you would like test requests from [Loadmill](https://www.loadmill.com) to be sent to it during a load test. However, if we allow _**anyone**_ to send requests to `myapp.com` it could be abused by a malicious user to attack your servers by flooding them with requests.

The way this problem is solved is by using **domain verification**, a simple process in which you are asked to:

1. Go to **Account Settings &gt; Domains**.
2. Enter your domain host name \(including subdomains\) in the text area at the top of the page and click **Verify**.
3. You will be promped and asked to host a small text file, containing a **Verification Token**, on your server in order to prove you own your domain, e.g.  `myapp.com/loadmill-challenge/aSnd5K8L86Pggg1rGLPgLlf6guK.txt`.
4. Once the file is hosted on your server, click **Verify** to complete the process.

# Express Middleware

If you are using [node.js](https://nodejs.org) and [express](https://expressjs.com), you can easily serve the verification file using our npm module: [express-loadmill](https://www.npmjs.com/package/express-loadmill).

It may also be used to enable [crowsourced load testing](testing-with-cors.html), for high volume load tests.


