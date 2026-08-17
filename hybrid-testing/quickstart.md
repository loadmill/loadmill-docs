# Web UI and Playwright Quickstart

This guide creates a small browser test with a Playwright step and runs it as a Loadmill flow.

## Before you start

You will need:

* A Loadmill account.
* A test suite with at least one flow.
* A Loadmill Desktop App or private agent with UI testing enabled.
* A web page that the execution environment can access.

## Add a Playwright step

1. Open a test suite and select a flow.
2. Add a new step and choose **Playwright**.
3. Enter the contents of a Playwright `test()` block. Do not include the `test()` declaration itself.

```ts
await page.goto('https://www.loadmill.com');
await expect(page).toHaveTitle(/Loadmill/);
```

4. Save the flow.
5. Run the test suite and inspect the step result.

The Playwright step receives a `page`, browser `context`, and `testInfo`. Suite and flow parameters are available directly as variables.

## Record instead of writing the first version

With the Loadmill Desktop App running, use **Record** in the Playwright step. Interact with the browser window that opens, then close it when the journey is complete. Loadmill adds the generated Playwright actions to the step so you can review and refine them.

## Continue

* Learn the supported [Playwright step syntax](../test-editor/steps/playwright-step.md).
* Run the flow across [multiple browsers](cloud-cross-browser-execution.md).
* Combine browser actions with API requests in a [hybrid flow](hybrid-api-ui-tutorial.md).
* Use [debug mode](debugging-playwright-tests.md) to step through a test locally.
