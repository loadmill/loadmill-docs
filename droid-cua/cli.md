# Droid CUA CLI

The Droid CUA desktop app is the main place to create and debug tests. The CLI lets you run saved `.dcua` tests from a terminal, CI pipeline, or other automation workflow across mobile, cloud device, and web targets.

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

## Choose an LLM provider and CUA model

### Use Loadmill (default)

The CLI uses Loadmill by default, with `loadmill-smart` as the recommended, most robust model. You do not need to pass `--llm-provider` or `--cua-model` for a standard Loadmill run.

```sh
droid-cua \
  --avd adb:emulator-5554 \
  --instructions tests/login.dcua
```

### Use Loadmill Pulse for faster execution

For a faster, lower-cost Loadmill run, use `loadmill-pulse`. Loadmill is already the default provider, so you only need to set the model:

```sh
droid-cua \
  --cua-model loadmill-pulse \
  --avd adb:emulator-5554 \
  --instructions tests/login.dcua
```

`loadmill-beacon` is also available as an experimental Loadmill model.

### Use your own OpenAI API key

To use OpenAI instead of Loadmill, set `OPENAI_API_KEY` and explicitly pass `--llm-provider openai`. Passing an OpenAI model to `--cua-model` alone does not change the provider.

Choose `gpt-5.6-terra`, `gpt-5.6-luna`, or `gpt-5.4`.

```sh
OPENAI_API_KEY=your-openai-api-key \
droid-cua \
  --llm-provider openai \
  --cua-model gpt-5.4 \
  --avd adb:emulator-5554 \
  --instructions tests/login.dcua
```

For CI or a config file, use `"llmProviderMode": "openai"` to select OpenAI. You can also set `DROID_CUA_LLM_PROVIDER=openai` as the default provider for a shell environment.

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

## Run a saved web test

Use `--target web` to run a `.dcua` test against an installed browser.

```sh
droid-cua --target web --browser chrome --instructions tests/search.dcua
```

Supported browser values are `chrome` and `edge`.

Local web runs use a persistent browser profile by default. Pass `--session-mode fresh` for an independent temporary profile:

```sh
droid-cua \
  --target web \
  --browser chrome \
  --session-mode fresh \
  --instructions tests/search.dcua
```

See [Web Testing with Droid](web-testing.md) for browser setup, saved-test examples, and the boundary between the web page and browser controls.

***

## Run on a LambdaTest cloud device

Set your LambdaTest credentials:

```sh
export LAMBDATEST_USERNAME=your-username
export LAMBDATEST_ACCESS_KEY=your-access-key
```

Then run with `--device-source lambdatest` and pass the target device details.

```sh
droid-cua \
  --device-source lambdatest \
  --platform android \
  --device-name "Galaxy S24" \
  --os-version "14" \
  --app ./app-debug.apk \
  --instructions tests/login.dcua
```

Android cloud runs require an `.apk` file. iOS cloud runs require an `.ipa` file.

***

## Run on Loadmill Cloud

Loadmill Cloud lets you run saved Droid CUA tests on cloud-hosted Android or iOS devices. It is a paid feature; contact [Loadmill Support](mailto:support@loadmill.com) to enable it for your account before setting it up.

After Loadmill Cloud is enabled, create a Loadmill API token and make it available to your local shell or CI environment:

```sh
export LOADMILL_API_TOKEN=your-loadmill-api-token
```

Start a run with `--device-source loadmill-cloud`, the target platform, device name, OS version, app build, and a saved test:

```sh
droid-cua \
  --device-source loadmill-cloud \
  --platform android \
  --device-name "Galaxy S24" \
  --os-version "14" \
  --app ./app-debug.apk \
  --instructions tests/login.dcua
```

Use an `.apk` app build for Android or an `.ipa` app build for iOS.

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
  "llmProviderMode": "loadmill",
  "cuaModel": "loadmill-smart",
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
| `--target` | Target kind, such as `mobile` or `web`. |
| `--instructions` | Path to a `.dcua` test file or a folder of `.dcua` files. |
| `--avd` | Android device, Android emulator, or iOS simulator name. |
| `--platform` | Target platform, such as `android` or `ios`. |
| `--browser` | Browser for web runs, such as `chrome` or `edge`. |
| `--session-mode` | Local web session mode: `persistent` (default) or `fresh`. |
| `--device-source` | Mobile device source, such as `local`, `lambdatest`, or `loadmill-cloud`. |
| `--device-name` | Cloud device name for LambdaTest or Loadmill Cloud. |
| `--os-version` | Cloud device OS version for LambdaTest or Loadmill Cloud. |
| `--app` | App build path for cloud runs. Use `.apk` for Android or `.ipa` for iOS. |
| `--config` | Path to a Droid CUA headless config file. |
| `--llm-provider` | AI provider for the run: `loadmill` (default) or `openai`. Set this to `openai` when using your own OpenAI API key. |
| `--cua-model` | Model to use for the run. With Loadmill, use `loadmill-smart` (recommended and most robust), `loadmill-pulse` (faster and lower cost), or experimental `loadmill-beacon`. With OpenAI, use `gpt-5.6-terra`, `gpt-5.6-luna`, or `gpt-5.4`. |
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
```

A successful run exits with code `0`. A failed run exits with code `1`, so CI can fail the build when the mobile test fails.
