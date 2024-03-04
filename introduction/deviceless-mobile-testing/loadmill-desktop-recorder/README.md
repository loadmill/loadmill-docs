# Loadmill desktop recorder

Loadmill Desktop Recorder is a powerful tool designed to simplify and enhance your deviceless testing experience. By capturing user interactions with your application at the API level, the Desktop Recorder allows you to quickly and efficiently create end-to-end API-driven test flows.&#x20;

There are three main components that work together to provide a powerful and efficient testing solution:

1. **Loadmill UI**: Same as the web interface for managing your testing process. With the Loadmill UI, you can edit and execute test flows, and access reporting and run results.\
   ![](<../../../.gitbook/assets/image (29) (2).png>)
2. **MITM Proxy**: The integrated Man-in-the-Middle (MITM) proxy allows you to capture API traffic from your mobile device by intercepting the communication between the device and the backend servers. \
   ![](<../../../.gitbook/assets/image (25) (2).png>)
3. **Loadmill Agent**: The Loadmill Agent enables local execution of test scenarios, allowing you to run tests directly from your computer within your network. This feature simplifies the testing process and makes it more accessible, allowing you to quickly and easily debug tests and obtain results.

{% hint style="info" %}
The agent is controlled by the play/stop button integrated to the top right corner of the application.
{% endhint %}

## **Proxy area (Recorder section)**

**General controls:**&#x20;

<figure><img src="../../../.gitbook/assets/image (13) (2).png" alt=""><figcaption></figcaption></figure>

At the top, you can find controls for:&#x20;

* starting/pausing the proxy
* Importing har file, to continue the work
* Clearing the list
* Listening IP+Port information
* Certificate download
* Filtering area
* Destination suite for generated tests

**Proxy entries area:**

<figure><img src="../../../.gitbook/assets/image (8) (2).png" alt=""><figcaption></figcaption></figure>

Once started and configured, the proxied requests will be collected in the list.\
The controls in the list allow:\
&#x20;\- Viewing a request details by clicking on it\
&#x20;\- Deleting requests by selecting them\
&#x20;\- Exporting har file

**Test creation controls:**\
![](<../../../.gitbook/assets/image (14) (2).png>)\


Bottom right area

* Analyze button - will mark out irrelevant requests, the user can revert this decision by clicking the <img src="../../../.gitbook/assets/image (30) (2).png" alt="" data-size="line"> button at the top of the entries area.
* Create test button - will process the requests and generate parameterized test in loadmill.\
  (The test will be found according to the suite selector by switching to loadmill <img src="../../../.gitbook/assets/image (12) (2).png" alt="" data-size="line"> area)
