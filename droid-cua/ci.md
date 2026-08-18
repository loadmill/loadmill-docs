# Running Droid Tests in CI

Saved Droid tests can run from a CI pipeline through the Droid CUA CLI. Build and stabilize a test in the desktop app first, commit the `.dcua` test and its context files to your repository, and then run the same test headlessly in CI.

## Before you start

You will need:

* A saved `.dcua` test that passes reliably.
* The Droid CUA CLI installed in the CI environment.
* A device target. Cloud devices are usually the simplest choice for hosted CI runners.
* Any required Loadmill, device-provider, or AI-provider credentials stored as CI secrets.
* The tested `.apk` for Android cloud runs or `.ipa` for iOS cloud runs.

See the [CLI guide](cli.md) for all device sources, credentials, and command options.

## Keep CI configuration in the repository

Use a small JSON configuration file to keep the model, application context, and prompt settings consistent between local and CI runs.

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

Start with `loadmill-smart` while creating and stabilizing a test. After the test is reliable, consider switching routine runs to `loadmill-pulse` for faster, lower-cost execution.

## Example cloud run

Store the Loadmill API token as a protected CI secret and expose it to the command as `LOADMILL_API_TOKEN`.

```sh
npm install -g @loadmill/droid-cua

droid-cua \
  --device-source loadmill-cloud \
  --platform android \
  --device-name "Galaxy S24" \
  --os-version "14" \
  --app ./app-debug.apk \
  --instructions tests/login.dcua \
  --config ci/droid-cua.json \
  --debug
```

Loadmill Cloud must be enabled for the account. You can also use a configured LambdaTest device or a local device available to a self-hosted runner.

## Use the process exit code

A successful Droid run exits with code `0`. A failed run exits with code `1`, allowing the CI job to fail when the test does not complete successfully.

Keep detailed artifacts for failed runs by using `--debug`. Use `--record` when screenshots from the complete run are useful for investigation.

Uploaded CI results also appear in the shared [Droid Runs dashboard](runs-dashboard.md), where the team can filter by project, source, and platform and open the detailed report.
