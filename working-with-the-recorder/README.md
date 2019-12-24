# Recordings

![](../.gitbook/assets/image%20%283%29.png)

Loadmill recordings allow you to capture live traffic in your QA or Production environment and replay it as API tests.

The traffic is split to different sessions by its source \(different IPs\) and intermissions between user actions. 

In order to record traffic in a specific environment you first need to install the Loadmill recorder as detailed in the next section.

![](../.gitbook/assets/image%20%2811%29.png)

## Loadmill's Recording Chrome Extension

{% embed url="https://youtu.be/XhaFuC\_mY8A" caption="Loadmill Recorder Demo " %}

### How to use Chrome dev tools to record a Loadmill API test:

* Download the [Loadmill recorder extension](https://chrome.google.com/webstore/detail/loadmill-recorder/gdkmnfehipofdefhpegbgkkocinlaofd)
* Open the Chrome Developer Tools and switch to the Loadmill Rec tab.
* If you are not logged in to Loadmill, you will be prompted to the login page
* Create a Test suite in Loadmill that will hold our recorded flows, and select it in the extension. 
* Clear the captured requests list and navigate to the tested website.
* Use the filter and the request's delete buttons to filter out irrelevant requests. 
* When you are done recording your session click the "Upload" button at the bottom.

## Additional supported recording methods 

In case you're already using a recording solution and would like Loadmill to generate an API Test Suite from it, the following recording methods can be imported to Loadmill :

1. [GoReplay](https://goreplay.org/): An open-source network monitoring tool which can record your live traffic, and use it for shadowing, load testing, or detailed analysis and monitoring.
2. [HAR file](https://en.wikipedia.org/wiki/HAR_%28file_format%29): Use the browser's Dev Tools to record a HAR file. 
3. [Charles proxy](https://www.charlesproxy.com/): An HTTP proxy that enables a developer to view all of the HTTP and SSL / HTTPS traffic between their machine and the Internet. Export sessions to HAR files and import them as Loadmill tests.

