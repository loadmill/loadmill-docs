# API-First End-to-End Testing

API-first end-to-end testing validates complete business processes through the network interactions produced by real user or system behavior. Instead of relying on the UI for every execution, Loadmill captures the underlying API traffic, identifies dependencies between requests, and turns the behavior into a reusable test flow.

This approach is useful when a journey crosses several services or applications. The generated flow represents the business process while running quickly and deterministically at the API layer.

## How it works

1. Perform a real workflow in a web or mobile application.
2. [Capture the resulting API traffic](../user-behavior-testing/working-with-the-recorder.md).
3. Filter requests that do not belong to the scenario.
4. Let Loadmill identify values that must be extracted and reused between requests.
5. Review the generated flow in the [Test Editor](../test-editor/layout.md).
6. Run the flow manually, from CI, or as part of a test plan.

## Ways to create API tests

You can record browser traffic with the [Loadmill Test Composer](../loadmill-test-composer/quickstart.md), capture traffic from a mobile app with [Mobile API Testing](../introduction/deviceless-mobile-testing/README.md), import recorded traffic, or create request steps directly in the Test Editor.

## Where to go next

* Follow the [API-first E2E quickstart](../quick-guide/quick-start-guide.md) for a complete example.
* [Register your first API flow](../quick-guide/register-your-first-api-flow.md).
* Learn how [contract testing](../introduction/api-server-testing/contract-testing.md) and [regression testing](../introduction/api-server-testing/regression-testing.md) fit into API coverage.
* Use the [Test Editor reference](../test-editor/layout.md) when building more advanced flows.
