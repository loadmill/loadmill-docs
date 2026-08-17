# Cloud and Cross-Browser Execution

Loadmill can execute the same Playwright flow across multiple browser configurations. This is useful when a journey must behave consistently across browser engines, desktop sizes, or mobile browser profiles.

## Select browser coverage

1. Open a flow containing a Playwright step.
2. Open the Playwright step settings.
3. Select the browser and device configurations you want to test.
4. Save and run the test suite.

Loadmill provisions the selected browser environments and includes each execution in the run results.

## Start with purposeful coverage

Use the smallest browser set that represents the environments your users depend on. Add configurations when they protect a real compatibility risk rather than selecting every available browser for every run.

A common pattern is to use one primary browser for pull-request feedback and a broader browser matrix for scheduled or release runs.

## Keep setup outside the browser when possible

Cross-browser suites multiply the cost of repeated UI actions. Use API steps to create data or establish state, then keep the Playwright portion focused on the browser-specific behavior you need to validate. See the [Hybrid API and UI Tutorial](hybrid-api-ui-tutorial.md).

For the complete set of browser features, see [Playwright Integration Capabilities](capabilities.md).
