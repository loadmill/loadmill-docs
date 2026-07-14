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

### Use Loadmill Beacon for faster execution

For a faster, lower-cost Loadmill run, use `loadmill-beacon`. Loadmill is already the default provider, so you only need to set the model:

```sh
droid-cua \
  --cua-model loadmill-beacon \
  --avd adb:emulator-5554 \
  --instructions tests/login.dcua
```

### Use your own OpenAI API key

To use OpenAI instead of Loadmill, set `OPENAI_API_KEY` and explicitly pass `--llm-provider openai`. Passing an OpenAI model to `--cua-model` alone does not change the provider.

Choose `gpt-5.4` for the full model or `gpt-5.4-mini` for a faster OpenAI option.

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
| `--device-source` | Mobile device source, such as `local` or `lambdatest`. |
| `--device-name` | LambdaTest cloud device name. |
| `--os-version` | LambdaTest cloud device OS version. |
| `--app` | App build path for LambdaTest runs. Use `.apk` for Android or `.ipa` for iOS. |
| `--config` | Path to a Droid CUA headless config file. |
| `--llm-provider` | AI provider for the run: `loadmill` (default) or `openai`. Set this to `openai` when using your own OpenAI API key. |
| `--cua-model` | Model to use for the run. With Loadmill, use `loadmill-smart` (recommended and most robust) or `loadmill-beacon` (faster and lower cost). With OpenAI, use `gpt-5.4` or `gpt-5.4-mini`. |
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
