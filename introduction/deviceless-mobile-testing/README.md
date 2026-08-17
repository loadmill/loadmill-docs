# Mobile API Testing

Mobile API testing captures the network traffic produced while someone uses a mobile app and turns that traffic into reusable API-first test flows. The initial scenario is performed on a device, but the generated test validates the underlying services directly and does not need to repeat every action through the mobile UI.

This is different from [Droid mobile testing](../../droid-cua/README.md). Droid operates and validates the visible mobile interface. Mobile API testing uses a proxy to observe the app's requests and responses, then replays the business flow at the API layer.

## When to use mobile API testing

Use this approach when you want to:

* Build fast regression coverage from real mobile behavior.
* Validate a business journey across several backend services.
* Capture dynamic IDs, tokens, and other values passed between requests.
* Reuse the resulting API flow in CI or as the basis for a performance test.

Use Droid instead when the mobile interface, visual state, or device interaction is the behavior you need to validate.

## How it works

1. The Loadmill Desktop App runs a proxy on your computer.
2. A mobile device is configured to send its network traffic through that proxy.
3. You perform the scenario in the mobile app.
4. Loadmill records the relevant requests and responses.
5. The Desktop Recorder analyzes the capture and generates a parameterized API test flow.
6. You review, run, and maintain the flow in Loadmill.

<figure><img src="../../.gitbook/assets/image (50).png" alt="Mobile application traffic captured through the Loadmill proxy"><figcaption><p>Mobile application traffic is captured and converted into an API-first test flow.</p></figcaption></figure>

## Before you start

You will need:

* A mobile app and device you can use for the capture.
* A Mac or Windows computer running the Loadmill Desktop App.
* The computer and mobile device connected to the same network.
* Permission to install the Loadmill certificate and configure the device's Wi-Fi proxy.

## Capture your first flow

1. [Install the Loadmill Desktop App](installing-loadmill-desktop-app/README.md).
2. [Install the Loadmill certificate](installing-certificate-on-mobile-devices/README.md) on the mobile device.
3. [Configure the mobile proxy](configuring-proxy-on-mobile-devices/README.md).
4. [Capture the mobile API traffic](capturing-traffic-with-loadmill-mitm-proxy.md).
5. Use the [Loadmill Desktop Recorder](loadmill-desktop-recorder/README.md) to filter the capture and [generate a test flow](loadmill-desktop-recorder/generating-test-flows.md).

If traffic is not appearing or the app cannot connect, see [Mobile Capture Troubleshooting](troubleshooting.md).
