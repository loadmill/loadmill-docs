# Domain Verification

**Domain verification** is the process of verifying that your domain or hostname actually belongs to you, so we can load-test it.

For example, if you have an app hosted on `myapp.com` you would like test requests from [Loadmill](https://www.loadmill.com) to be sent to it during a load test. However, if we allow _**anyone**_ to send requests to `myapp.com` it could be abused by a malicious user to attack your servers by flooding them with requests.

The way this problem is solved is by using **domain verification**, a simple process in which you are asked to:

1. Go to **User Settings &gt; Domains**.
2. Enter the hostname or sub-domain you would like to test in the text area at the top of the page and click **Verify**.
3. You will be prompted and asked to host a small text file, containing a **Verification Token**, on your server in order to prove you own your domain, e.g.  `myapp.com/loadmill-challenge/aSnd5K8L86Pggg1rGLPgLlf6guK.txt`.
4. Once the file is hosted on your server, click **Verify** to complete the process.

If you have access to your site's **DNS configuration**, you can [prove ownership without changing code on your server](domain-verification.md#dns-verification).

**Note:** There is no need to prove ownership of a sub-domain once its parent is verified. For instance, if you have already completed the verification process for `myapp.com` you may load-test `www.myapp.com` or `blog.myapp.com` as well.

## Express Middleware

If you are using [node.js](https://nodejs.org) and [express](https://expressjs.com), you can easily serve the verification file using our npm module: [express-loadmill](https://www.npmjs.com/package/express-loadmill).

It may also be used to enable [crowsourced load testing](testing-with-cors.md), for high volume load tests.

## DNS Verification

If you do not want or unable to serve a file on your server, you can prove ownership of your domain via DNS.

According to the documentation of your hosting service or DNS provider, add a DNS record of the following format:

* **Type:** `TXT`
* **Name:** The sub-domain you would like to test, e.g. `www` or `myapp.com`
* **Value:** `loadmill-challenge=<VERIFY_TOKEN>` where `<VERIFY_TOKEN>` stands for the **Verification Token** you were asked to serve in a text file. E.g. `loadmill-challenge=aSnd5K8L86Pggg1rGLPgLlf6guK`

You can make sure that the text record was properly added by looking it up using DNS lookup tools like this one - [MxToolbox](https://mxtoolbox.com/TXTLookup.aspx)

Once the DNS record is set, click **Verify** to complete the process.

**Note:** DNS records may take a while to propogate, so if the verification initially fails, try again after a few minutes.

