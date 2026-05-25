# Droid CUA CLI

The Droid CUA desktop app is the main place to create and debug tests. The CLI lets you run saved `.dcua` tests from a terminal, CI pipeline, or other automation workflow.

***

## Install the CLI

Install the package globally:

```sh
npm install -g @loadmill/droid-cua
```

Then run:

```sh
droid-cua
```

***

## Run a saved Android test

Use `--instructions` to point at a `.dcua` file and `--avd` to select the target device or emulator.

```sh
droid-cua --avd adb:emulator-5554 --instructions tests/login.dcua
```

You can also point `--instructions` at a folder. Droid CUA will run the `.dcua` files in that folder.

```sh
droid-cua --avd adb:emulator-5554 --instructions tests
```

***

## Run a saved iOS simulator test

On macOS, use `--platform ios` and pass the simulator name:

```sh
droid-cua --platform ios --avd "iPhone 16" --instructions tests/login.dcua
```

***

## Use a config file

For CI, it is recommended to keep a small JSON config file in the repository and run tests with `--config`.

```sh
droid-cua \
  --avd adb:emulator-5554 \
  --instructions tests/login.dcua \
  --config ci/droid-cua.json \
  --debug
```

Example config:

```json
{
  "cuaModel": "gpt-5.4",
  "promptCustomizations": {
    "basePromptInstructions": "",
    "designModeInstructions": "",
    "executionModeInstructions": ""
  },
  "appContextEnabled": true,
  "appContextPath": "../tests/context.md",
  "contextOptimizationEnabled": true,
  "contextOptimizationThreshold": 30000
}
```

The config file keeps prompt settings and app context consistent between local runs and CI runs.

***

## Common CLI options

| Option | Description |
| --- | --- |
| `--instructions` | Path to a `.dcua` test file or a folder of `.dcua` files. |
| `--avd` | Android device, Android emulator, or iOS simulator name. |
| `--platform` | Target platform, such as `android` or `ios`. |
| `--config` | Path to a Droid CUA headless config file. |
| `--cua-model` | Model to use for the run. |
| `--context` | Path to an app context file. |
| `--no-context` | Disable app context for the run. |
| `--record` | Save screenshots from the run. |
| `--debug` | Write detailed debug artifacts for troubleshooting. |

***

## CI basics

In CI, install the CLI, provide the required credentials as secrets, and run the saved test file with a config file.

```yaml
jobs:
  droid-cua:
    runs-on: ubuntu-latest
    steps:
      - uses: actions/checkout@v4
      - uses: actions/setup-node@v4
        with:
          node-version: 20
      - run: npm install -g @loadmill/droid-cua
      - run: |
          droid-cua \
            --avd adb:emulator-5554 \
            --instructions tests/login.dcua \
            --config ci/droid-cua.json \
            --debug
        env:
          OPENAI_API_KEY: ${{ secrets.OPENAI_API_KEY }}
```

A successful run exits with code `0`. A failed run exits with code `1`, so CI can fail the build when the mobile test fails.
