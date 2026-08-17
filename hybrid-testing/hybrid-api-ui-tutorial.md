# Hybrid API and UI Tutorial

A hybrid flow uses API steps for fast setup or backend validation and UI steps for behavior that must be observed in the browser. This example outlines a common pattern: create data through an API, verify it through the UI, and confirm the resulting state through another API request.

## Before you start

Create a test suite and a flow, then make sure a Loadmill Desktop App or private agent with UI testing enabled is available.

## Step 1: Prepare state through an API

Add a [Request step](../test-editor/steps/request-editor.md) that creates the data needed by the scenario. Extract any value the UI step needs, such as an item ID, email address, or generated name.

API setup is usually faster and less fragile than navigating several browser screens before reaching the behavior under test.

## Step 2: Validate the browser journey

Add a [Playwright step](../test-editor/steps/playwright-step.md) after the request. Open the relevant page, locate the data created by the API step, perform the important user action, and assert the visible result.

Suite and flow parameters are available directly as variables in the Playwright code. Cookies created by earlier steps are passed to the browser context automatically.

```ts
await page.goto(targetUrl);
await page.getByText(createdItemName).click();
await expect(page.getByText('Completed')).toBeVisible();
```

You can use a [UI Agent step](../test-editor/steps/ui-agent-step.md) instead when the browser portion is better described as a goal in natural language.

## Step 3: Verify the final state

Add another Request step to retrieve the updated resource and assert the backend state. This separates visible UI validation from deeper data validation while keeping both in one end-to-end flow.

## Step 4: Run and refine

Run the complete suite. If the browser step needs investigation, use [debug mode](debugging-playwright-tests.md). Once the flow is stable, connect it to your [CI workflow](../integrations/npm-modal.md).
