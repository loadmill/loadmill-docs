# Web UI and Hybrid Testing

Loadmill supports browser testing with Playwright and natural-language UI Agent steps. You can create UI-only tests or combine browser actions with API requests in the same flow.

Hybrid testing keeps UI coverage focused on behavior that must be observed in the browser. API steps can prepare data, authenticate users, or validate backend state, while Playwright or the UI Agent handles the visible user journey.

## Choose a UI step

Use a [Playwright step](../test-editor/steps/playwright-step.md) when you want exact, reviewable browser automation code and direct control over interactions and assertions.

Use a [UI Agent step](../test-editor/steps/ui-agent-step.md) when you want to describe a browser goal and its validation in natural language. The agent interprets the visible page and works toward that goal.

## Why combine API and UI steps?

Browser tests become slower and more fragile when every setup action must happen through the UI. A hybrid flow can create the required state through an API, validate the user-facing behavior in the browser, and verify the final state through another API request.

This keeps the test close to the business journey while reducing unnecessary UI interactions.

## Get started

* Follow the [Web UI and Playwright Quickstart](quickstart.md).
* Build a combined flow with the [Hybrid API and UI Tutorial](hybrid-api-ui-tutorial.md).
* Review the complete [Playwright integration capabilities](capabilities.md).
* Use the [Agent Testing Quickstart](../quick-guide/agent-testing-quick-guide.md) for a natural-language web flow.
