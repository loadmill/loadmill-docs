# UI Agent step

The **UI Agent step** allows you to automate UI interactions using natural language prompts. Instead of writing code, you describe what you want the agent to do, and it autonomously navigates your application, performs actions, and validates results.

This is especially useful for quickly creating end-to-end tests, validating user flows, and testing complex UI interactions without writing any automation code.

![UI Agent step editor](<../../assets/ui-agent-step-example.png>)

## Step structure

The UI Agent step consists of three main parts:

### 1. Navigate to URL

The starting point for the agent. This is the URL the browser navigates to when the step begins.

**Example:**
```
https://example.com/login
```

### 2. Actions (optional)

Instructions describing the actions the agent should perform before reaching the UI state you want to validate. This field is optional — if you only need to validate something on the page without performing any actions, you can leave it empty.

Use this to describe interactions such as:
- Clicking buttons or links
- Filling out forms
- Navigating through menus
- Scrolling or hovering

**Example:**
```
Enter "user@example.com" in the email field and "password123" in the password field, then click the Login button.
```

### 3. Validation

Describe what you want to verify on the UI state after the actions are complete. This is where you specify the expected outcome of the test.

Common validations include:
- Verifying an element is visible
- Checking that a button is clickable
- Confirming an item was deleted or removed
- Validating that specific text or content is displayed
- Ensuring error messages appear (or don't appear)

**Example:**
```
Verify that the dashboard page is displayed and the welcome message shows "Hello, User".
```

## Advanced settings

### Timeout

Configure the maximum time (in seconds) the agent is allowed to complete the step. If the step takes longer than the specified timeout, it will fail.

Set a reasonable timeout based on the complexity of your flow and the expected response time of your application.

## Parameters

You can use parameters in any of the UI Agent step fields. Parameters work the same way as in other parts of Loadmill — use the `${parameterName}` syntax, and the value will be resolved at runtime.

**Example:**
```
Enter "${userEmail}" in the email field and "${userPassword}" in the password field.
```

This allows you to:
- Reuse the same test with different data sets
- Reference values extracted from previous steps
- Use suite-level or flow-level parameters

## Viewing results

After running a test with UI Agent steps, you can view:

- **Step-by-step actions** the agent performed
- **Screenshots** captured during execution
- **Validation results** showing what passed or failed
- **Error details** if something went wrong

![UI Agent step run result](<../../assets/ui-agent-step-example-run.png>)

## Requirements

To use UI Agent steps, you need:

- A Loadmill account with AI Agent capabilities enabled
- The [Loadmill desktop app](https://app.loadmill.com/app/user/settings/desktop-app) installed and running

{% hint style="info" %}
UI Agent steps require the desktop app because the agent needs to control a real browser to interact with your application's UI.
{% endhint %}

## Related documentation

- [Agent Testing Quick Guide](../../quick-guide/agent-testing-quick-guide.md) - Get started with agent testing
- [Playwright step](playwright-step.md) - For code-based UI automation
