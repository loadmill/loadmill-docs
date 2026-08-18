# Testing Web Applications with Droid

Droid is primarily designed for mobile testing, but the same goal-oriented approach can operate a web application in Chrome or Edge. Web testing is useful when you want the agent to follow a realistic browser journey without maintaining selectors for every interaction.

Use Droid Web for flows where the visible experience and the route through the product matter. Use [Playwright](../hybrid-testing/overview.md) when you need precise DOM-level control, and use [API-first testing](../api-testing/overview.md) when the browser is not part of what you need to validate.

***

## Before you start

For local execution you need:

* The Droid CUA desktop app.
* Google Chrome or Microsoft Edge installed on the same computer.
* A Droid project containing your `.dcua` tests and optional `context.md`.

The setup wizard can verify that Droid detects the browser and can launch it through Playwright. Select **Web** on the wizard's Welcome step, complete the system checks, and run the browser setup probe.

For more information about the wizard, see [Getting Started](getting-started.md#complete-the-setup-wizard).

***

## Connect a local browser

Open **Devices** in the desktop app and:

1. Select **Web** as the platform.
2. Select **Local** as the source.
3. Choose an installed Chrome or Edge browser.
4. Choose a session mode.
5. Connect the browser.

| Session mode | Behavior | Good for |
| --- | --- | --- |
| **Persistent** | Reuses the Droid browser profile between sessions | Local development and flows that benefit from retained login state |
| **Fresh** | Starts with a clean temporary profile | Independent tests, authentication coverage, and repeatable CI-like runs |

Persistent mode does not remove the need to make the test's starting state clear. If login state is part of the behavior under test, use a fresh session and perform the login in the journey.

Accounts with Loadmill Cloud web access can also choose a hosted Chrome or Firefox browser and a browser version from the Devices page. Cloud availability depends on the account plan.

***

## Write a first web test

Start a saved web test with a `navigate:` instruction. This changes the page directly without asking the agent to operate the browser address bar.

```text
navigate: https://bank-demo.loadmill.com
Sign in as the maker account described in the project context.
Open the transfers page and create a transfer for $25.
Verify that the new transfer appears with the status "Pending".
```

The same instruction-writing guidance used for mobile applies to web tests: describe short-term goals, use visible product language, and define observable assertions.

### Understand the web boundary

The agent is active within the web page frame. It can interact with the site, follow links, type, scroll, and navigate as part of the test. It cannot use the browser's address bar, settings, bookmarks, extensions, or other browser chrome.

Use `navigate:` for a known starting URL and write the rest of the test as a journey through the application itself.

***

## Add web-specific context

Most shared product knowledge can remain in the same `context.md` used by mobile tests. Add web-specific guidance only when the browser experience differs in a non-obvious way, for example:

* Navigation moves from a bottom bar on mobile to a left sidebar on web.
* A menu opens only after hovering or clicking an account control.
* A table scrolls independently from the page.
* The responsive layout changes the names or locations of important controls.

Do not document browser settings or address-bar operations in project context because Droid cannot use those surfaces during the test.

***

## Run a saved web test from the CLI

Use `--target web`, choose the installed browser, and point `--instructions` at the test:

```sh
droid-cua \
  --target web \
  --browser chrome \
  --session-mode fresh \
  --instructions tests/transfer.dcua
```

Supported local browser values are `chrome` and `edge`. The CLI runs saved web tests; it does not provide an interactive web shell.

See the [CLI reference](cli.md#run-a-saved-web-test) for additional options.

***

## Choose the right web testing layer

Start with Droid Web when the test should read like a user journey and adapt to the visible interface. Choose another layer when the test's purpose is different:

| Need | Recommended approach |
| --- | --- |
| Validate a realistic goal through the visible browser experience | Droid Web |
| Combine an adaptive UI journey with API state preparation | Loadmill flow followed by Droid Web |
| Assert exact DOM behavior or use precise locator-level interactions | Playwright |
| Exercise many backend inputs without validating the page | Loadmill API testing |

For more guidance on scope and data variation, see [Common Droid Testing Mistakes](common-mistakes.md#testing-backend-permutations-through-the-ui).
