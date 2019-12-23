# Embedding the recording service worker

### What is a service worker <a id="what_is_a_service_worker"></a>

A service worker is a script that your browser runs in the background, separate from a web page, opening the door to features that don't need a web page or user interaction.

Service workers essentially act as proxy servers that sit between web applications, the browser, and the network. They are intended, among other things, to capture and inspect network requests.

### Recording website traffic using Loadmill

![Loadmill service-worker architecture](../.gitbook/assets/image%20%2814%29.png)

As shown in the diagram above, to record a website using the Loadmill service worker, you will have to embed the Loadmill SW on your page. However, due to security concerns, service workers can **not** be loaded from another domain. This means that you will have to host and serve the service worker file from your recorded server.

Another thing to consider is that service workers will only listen to events triggered in the same scope you have served the service worker from. For example — if you registered your Service Worker from _my-website.com/aaa_ the Service Worker will intercept all the _my-website.com/aaa/\*_ requests. Requests for _my-website.com/bbb/\*_ won’t be recorded!

### The TL;DR

* Make sure that your service worker registration script is embedded in every page your users might visit.
* A good place to embed the recorder script is usually where you injected your google analytics script tag.
* The service worker script file has to be loaded from the recorded application domain. \(usually hosted on your server\)
* It is best to load the service worker from the root path of the recorded application, i.e. _my-website.com/loadmill-worker.js **and not** from my-website.com/wubba/lubba/dub/dub/loadmill-worker.js_
* If your website is using a strict [Content Security Policy \(CSP\)](https://developer.mozilla.org/en-US/docs/Web/HTTP/CSP), you should add these two domains to the list of allowed domains `https://sdk.amazonaws.com` and `https://*.loadmill.com`. In case the Loadmill recorder fails to load because of a CSP problem, you should see the following error message in the console logs-

![CAP console error](../.gitbook/assets/image%20%2812%29.png)

