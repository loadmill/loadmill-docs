# Deviceless mobile testing

## Deviceless Mobile Testing with Loadmill

Deviceless testing is a revolutionary approach to testing that focuses on capturing user behavior from mobile devices. By creating end-to-end API-driven flows, you can execute tests quickly and efficiently without the need for a physical device. Loadmill utilizes AI algorithms and the Codex engine to understand user behavior and build dynamic flows that can be executed repeatedly, taking into account dynamic values such as IDs and keys.

### Why Deviceless Testing?

Traditional testing methods require physical devices or emulators to run tests, which can be time-consuming and resource-intensive. Deviceless testing offers several advantages:

1. **Speed**: Deviceless testing allows for faster test execution since it bypasses the need for a device or emulator.
2. **Scalability**: You can execute multiple tests concurrently, enabling you to scale your testing efforts effortlessly.
3. **Cost-effective**: Reduces the need for purchasing and maintaining a wide range of devices for testing purposes.
4. **Reliability**: API-driven tests are less prone to errors caused by device-specific issues or UI changes.

### How Loadmill's Deviceless Testing Works

Loadmill's deviceless testing solution leverages AI algorithms to create dynamic flows based on user behavior. The process consists of the following steps:

1. **Capturing User Behavior**: Loadmill captures user interactions from a mobile device with your application at the API level. This includes requests, responses, and any relevant metadata.
2. **Analyzing Data**: The captured data is analyzed by loadmill's AI algorithms to identify patterns, correlations, and dependencies between different API calls.
3. **Generating Dynamic Flows**: Based on the analysis, Loadmill generates end-to-end API-driven flows that accurately represent user behavior. These flows are designed to be dynamic, taking into account variable values that may change between test executions.
4. **Executing Tests**: The generated flows can be executed as test scenarios within Loadmill. You can run these tests concurrently, allowing you to scale your testing efforts and obtain results quickly.
5. **Monitoring and Reporting**: Loadmill provides real-time monitoring and reporting features, enabling you to track test progress, identify issues, and measure performance metrics.\


<figure><img src="../../.gitbook/assets/image (50).png" alt=""><figcaption><p>A conceptual diagram of Loadmill fed through MITM proxy to capture mobile behavior</p></figcaption></figure>

### Getting Started with Deviceless Testing in Loadmill

To start using deviceless testing with Loadmill, follow these steps:

1. **Get access to Loadmill:** If you haven't already, [contact us](https://www.loadmill.com/request-access/) to get an account.
2. **Download and install Loadmill Desktop App**: To begin with deviceless testing, download the Loadmill Desktop App at [https://github.com/loadmill/desktop-app/releases/latest](https://github.com/loadmill/desktop-app/releases/latest). (This application includes a built-in MITM proxy that will allow you to capture traffic from your mobile device.)
3. **Configure your device and app to use Loadmill's MITM proxy**: In order to capture the API traffic, you need to configure your mobile device and app to communicate through the Loadmill MITM proxy. This can be done by modifying the Wi-Fi settings on your device and updating the app's network configuration, if necessary. Ensure that your mobile device is connected to the same network as your computer running the Loadmill Desktop App.

<figure><img src="../../.gitbook/assets/image (121).png" alt=""><figcaption><p>Loadmill desktop application with MITM proxy shows traffic of a mobile app</p></figcaption></figure>

