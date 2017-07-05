# Domain Verification

**Domain verification** is the process of verifying that your domain actually belongs to you, so we can load-test it.

For example, if you have an app hosted on `myapp.com` you would like test requests from [Loadmill](https://www.loadmill.com) to be sent to it during a load test. However, if we allow _**anyone**_ to send requests to `myapp.com` it could be abused by malicious user to attack your servers by flooding it with requests.

The way this problem is solved is by using **domain verification**, a simple process in which you are asked to:

1. Go to **Account Settings &gt; Domains** and enter your domain host name \(including subdomains\) in the text area at the top of the page.
2. Click **Verify**.
3. You will be promped and asked to host a small text file on your server in order to prove you own your domain. E.g. `myapp.com/loadmill-challenge/aSnd5K8L86Pggg1rGLPgLlf6guK.txt`.
4. Once the file is hosted on your server, click **Verify** to complete the process.

# Express MIddleware

If you are using \[node.js\]\(https://nodejs.org\) and \[express



