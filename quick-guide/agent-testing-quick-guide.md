# Agent Testing Quick Guide

This quick guide shows how to get access to Loadmill Agent Testing, create a simple agent-based test, and run it against a real web UI from the desktop app.

***

## Before you start

You will need:

* A Loadmill account
* A plan that supports AI Agent capabilities (if you have a promo code, you can use it during sign-up to activate access)
* The Loadmill desktop app installed

***

## Step 1: Sign up and activate access

Create your account here: [Sign up to Loadmill](https://app.loadmill.com/app/signup)

*If you already have a Loadmill account, you can skip the sign-up part of this step.*

If you received a promo code by email, open [Billing](https://app.loadmill.com/app/user/settings/billing) after signing in and apply the code there. This enables access to the Agent step for eligible accounts.

Open the Billing page from your account settings.

![Billing page showing the subscription plan section](<../assets/billing-page.png>)

Enter the promo code and activate it.

![Billing page showing the subscription code activation field](<../assets/promo-code.png>)

***

## Step 2: Download the desktop app

Download the desktop app here: [Loadmill desktop app](https://app.loadmill.com/app/user/settings/desktop-app)

**Important:** The desktop app is required to run Agent steps.

*If you already have the desktop app installed, you can skip this step.*

***

## Step 3: Create your first agentic test

1. Open the Loadmill desktop app and create a new test suite.
2. Add a new step and choose **UI Agent**.

![Add a new UI Agent step](<../assets/add-ui-agent-step.png>)

3. Enter a short prompt that describes the user flow you want the agent to perform on your site and what it should validate.

![Example of a UI Agent step configured in a test](<../assets/ui-agent-step-example.png>)

4. Run the test you created.

![Example of a UI Agent step run result](<../assets/ui-agent-step-example-run.png>)

This is the fastest way to get started: give the agent a short, real UI task and validate that it can complete it reliably.

{% hint style="info" %}
Keep the first run simple. Start with one short path on your site so you can watch how the agent navigates the UI and validate the result.
{% endhint %}

***

## Learn more about creating tests in Loadmill

Agent Testing is a fast way to validate real user flows, but it works best as part of Loadmill's broader API-first testing approach.

If you are new to Loadmill, you can also learn how to create tests with the Loadmill Composer and generate API tests from real user activity. See the [Quick Start Guide](quick-start-guide.md) for a step-by-step walkthrough.

***

## Need help?

If you have any questions or need help, contact us at [support@loadmill.com](mailto:support@loadmill.com).

If you would like to book a demo, click [here](https://www.loadmill.com/book-a-demo).
