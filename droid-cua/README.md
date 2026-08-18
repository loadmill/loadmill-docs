# Droid Mobile Testing

Droid CUA is Loadmill's AI-powered desktop app for mobile and web testing.

It helps you create, run, and manage tests for Android devices and emulators, iOS simulators on macOS, cloud mobile devices, and browser flows. Instead of writing traditional automation code with selectors and locators, you describe the user flow in natural language and let the agent operate the app from the screen, the same way a person would.

With Droid CUA you can:

* Connect to a real Android device, Android emulator, iOS simulator, cloud mobile device, or browser.
* Create mobile and web tests from plain-English instructions.
* Watch the agent execute each action with live logs.
* Save reusable `.dcua` test scripts.
* Run saved tests again from the desktop app or the CLI.
* Use local reports and the shared Droid Runs dashboard to review what happened.

***

## How it helps

Droid CUA is useful when you want to validate real mobile flows without spending time building and maintaining fragile selector-based scripts.

For example, you can ask the agent to sign in, search for an item, add it to the cart, submit a form, or verify that a confirmation screen is visible. Droid CUA captures the device screen, sends the screen and your instructions to the AI model, receives an action such as tap, scroll, type, or wait, and executes that action on the device.

The result is a test workflow that is easier to draft, easier to understand, and closer to how a real user interacts with your app.

***

## Platforms

### Android

Droid CUA supports physical Android devices and Android emulators.

### iOS

Droid CUA supports iOS simulators on macOS.

### Web

Droid CUA supports browser testing with installed Chrome or Edge.

### Cloud devices

Droid CUA supports cloud mobile runs from the CLI, including Loadmill Cloud and LambdaTest. Cloud runs use real Android or iOS devices and require the provider credentials plus an app build.

### Desktop support

* macOS: Android, iOS simulator, and web workflows
* Windows: Android and web workflows

***

## Learn more

* [Droid Mobile Testing Quickstart](getting-started.md)
* [Writing Reliable Droid CUA Tests](best-practices.md)
* [Common Droid Testing Mistakes](common-mistakes.md)
* [Testing Web Applications with Droid](web-testing.md)
* [Reviewing Droid Runs in Loadmill](runs-dashboard.md)
* [Setup](setup.md)
* [CLI](cli.md)
* [Running Droid Tests in CI](ci.md)
* [Agent Skill](skill.md)
