# Recordings

![](../.gitbook/assets/image%20%284%29.png)

Loadmill recordings allow you to capture traffic in your QA or Production environment and replay it as API tests.

![](../.gitbook/assets/image%20%2813%29.png)

There are several way to record user sessions:

### Record using Loadmill's Chrome Extension

{% embed url="https://youtu.be/XhaFuC\_mY8A" caption="Loadmill Recorder Demo " %}

#### How to use Chrome dev tools to record a Loadmill API test:

* Download the [Loadmill recorder extension](https://chrome.google.com/webstore/detail/loadmill-recorder/gdkmnfehipofdefhpegbgkkocinlaofd)
* Open the Chrome Developer Tools and switch to the Loadmill Rec tab.
* If you are not logged in to Loadmill, you will be prompted to the login page
* Create a Test suite in Loadmill that will hold our recorded flows, and select it in the extension. 
* Clear the captured requests list and navigate to the tested website.
* Use the filter and the request's delete buttons to filter out irrelevant requests. 
* When you are done recording your session click the "Upload" button at the bottom.

### Record multiple users by embedding a JavaScript recorder in your app

* Create a new recorded application in the [recording setup page](https://www.loadmill.com/app/recordings/setup)
* Follow the installation instructions in the application setup dialog

![](../.gitbook/assets/image%20%2821%29.png)

* After embedding the Loadmill worker recording script, reload the recored app and make sure the worker is loaded. In Chrome, open the browser developer tools and go to the Application tab and click ⚙️ Service Workers tab. See that there are no errors.

![](../.gitbook/assets/image%20%285%29.png)

* Create a new recording from the [recordings page in Loadmill.](https://www.loadmill.com/app/recordings/my-recordings) 
* Play your test scenarios in the recorded app. By default, the traffic is split to different sessions by its source \(different IPs\) and intermissions between user actions. \(If you with to manually split a recorded session in you test environment you can use the [Loadmill session splitter](https://chrome.google.com/webstore/detail/loadmill-session-splitter/beknfelcpakgnojjfcdpjddhnckekhni)\)
* When you're ready, stop the recording and generate a test suite from it. 

### Additional recording methods 

In case you're already using a recording solution and would like Loadmill to generate an API Test Suite from it, the following recording methods can be imported to Loadmill :

1. [GoReplay](https://goreplay.org/): An open-source network monitoring tool which can record your live traffic, and use it for shadowing, load testing, or detailed analysis and monitoring. You can import Gor files in the recording page by clicking IMPORT RECORDING.
2. [HAR file](https://en.wikipedia.org/wiki/HAR_%28file_format%29): Use the browser's Dev Tools to record a HAR file. You can import HAR files in the API and load test flow editor.
3. [Charles proxy](https://www.charlesproxy.com/): An HTTP proxy that enables a developer to view all of the HTTP and SSL / HTTPS traffic between their machine and the Internet. Export sessions to HAR files and import them as Loadmill test flows.

