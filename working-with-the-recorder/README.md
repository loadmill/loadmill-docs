# Recordings

![The Recordings tab](../.gitbook/assets/screenshot-35-.png)

Loadmill Recordings allow you to capture traffic in your QA or Production environment and replay it as API tests.

![](../.gitbook/assets/image%20%2819%29.png)

### Record multiple users by embedding a JavaScript recorder in your app

* Create a new recorded application in the [recording setup page](https://www.loadmill.com/app/recordings/setup)
* Follow the installation instructions in the application setup dialog

![](../.gitbook/assets/image%20%2828%29.png)

* After embedding the Loadmill worker recording script, reload the recored app and make sure the worker is loaded. In Chrome, open the browser developer tools and go to the Application tab and click ⚙️ Service Workers tab. See that there are no errors.

![](../.gitbook/assets/image%20%289%29.png)

* Create a new recording from the [recordings page in Loadmill.](https://www.loadmill.com/app/recordings/my-recordings) 
* Play your test scenarios in the recorded app. By default, the traffic is split to different sessions by its source \(different IPs\) and intermissions between user actions. \(If you with to manually split a recorded session in you test environment you can use the [Loadmill session splitter](https://chrome.google.com/webstore/detail/loadmill-session-splitter/beknfelcpakgnojjfcdpjddhnckekhni)\)
* When you're ready, stop the recording and generate a test suite from it. 

### 

