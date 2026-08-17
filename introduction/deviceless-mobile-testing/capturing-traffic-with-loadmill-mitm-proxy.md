# Capturing Mobile API Traffic

Loadmill's Desktop App uses a MITM (Man-in-the-Middle) proxy to capture API traffic from your mobile device. This records the requests and responses produced by a real mobile journey so Loadmill can generate a reusable API test flow.

{% hint style="info" %}
It is also possible to use 3rd party MITM proxies as well (ie. Charles proxy and proxyman) and export the captured traffic into loadmill.
{% endhint %}

The MITM proxy intercepts the communication between your mobile device and the backend servers, allowing Loadmill to analyze and record the API calls and responses. This approach ensures that you capture the most accurate and complete data for your testing scenarios.

To use the MITM proxy within Loadmill's Desktop App, follow these steps:

1. **Start the Loadmill Desktop App:** Switch to the proxy section \
   ![](<../../.gitbook/assets/image (120).png>) \
   at this stage the proxy will be paused without content.
2. **Install a Certificate**: Installing the Loadmill certificate on your device establishes a secure trust relationship between your device and the proxy, enabling it to decrypt the traffic for analysis and testing purposes.\
   In loadmill proxy, look for the following button ![](<../../.gitbook/assets/image (9) (2).png>) to download the certificate.
3. **Set up your mobile device** to use the proxy server provided by the Loadmill Desktop App. This typically involves configuring your device's Wi-Fi settings to use the proxy server's IP address and port number.
4. **Start the proxy:** By clicking the <img src="../../.gitbook/assets/image (22) (2).png" alt="" data-size="line">button
5. **Interact with your application:** you will see new requests accumulating in loadmill.\
   ![](<../../.gitbook/assets/image (7) (2).png>)
