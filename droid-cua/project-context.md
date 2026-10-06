# Project Context

`context.md` gives Droid the product knowledge it needs to understand your tests. Think of it as the brief you would give a new teammate: what the app does, what the important screens are called, and which details are easy to miss.

The `.dcua` file describes the journey to test. Context supplies the shared knowledge that helps Droid carry out that journey.

## Create and edit context

In the desktop app, select **Open app context** beside your project in the sidebar. If the file does not exist, Droid creates a starter `context.md` with sections for the app overview, screens, actions, and entities.

Edit it in Droid or in your usual text editor. Changes made in Droid are saved automatically to `context.md` in the project's root folder. It is an ordinary Markdown file that you can review and version alongside your tests.

```text
tests/droid/
├── context.md
├── catalog.dcua
└── checkout.dcua
```

All tests in the project, including tests in nested folders, use this shared context. Select the same project when starting Design Mode so Droid can use its context while exploring the app.

## What to include

Include stable information that helps Droid make a decision or recognize a result: product terminology, roles, navigation conventions, hidden gestures, or a screen that looks different from what its name suggests.

For example, a shopping app's context might contain:

```md
# Overview
Example Shop is a grocery app. Products and availability depend on the selected delivery area.

# Navigation
Delivery settings open from the location label at the top of the home screen.
The cart is available from the bottom navigation.

# Product details
Products have several package sizes. Use the full product name, including its size, to distinguish them.
The availability label on the product details screen is "In stock" or "Unavailable".

# Checkout
New delivery addresses appear at the bottom of a separately scrolling address list.
An order is complete when the confirmation screen shows "Order confirmed".
```

There is no required structure. Use short headings and clear sentences, and include only the parts of the product that matter to your tests. Specific facts are more useful than a long description of every screen.

## Build it while writing the test

Start with one journey and a small amount of context. When a run reveals something Droid needs to know, add it if another test or teammate would benefit from the same information.

If Droid struggles to find a newly added address, the scrolling behavior belongs in context. The particular address for that run belongs in [test data](data-driven-tests.md). The instruction to select it belongs in the test.

Aim for the minimum context that gives the agent the most useful guidance. Keep it current as the product changes. Leave out repeated test steps, irrelevant background, temporary workarounds, and information Droid can already read clearly on the screen. Put credentials in [`.secrets`](using-secrets.md).

For more on this approach, see [Writing Reliable Droid CUA Tests](best-practices.md#build-context-alongside-the-test).

## Use context in the CLI

Pass the file explicitly when running from a terminal:

```sh
droid-cua run tests/droid/catalog.dcua \
  --avd adb:emulator-5554 \
  --context tests/droid/context.md
```

You can also set `appContextPath` in a shared [CLI config file](cli.md#use-a-config-file). Paths in the config are relative to the config file's folder; a `--context` path is relative to the directory where you run the command.

For desktop execution, keep **App Context** enabled in Settings. In the CLI, `--no-context` disables it for that run. If Droid seems unaware of information you added, check that you selected the right project or supplied the correct file path, and that context is enabled.
