# Setup Troubleshooting

Use this page when Droid CUA cannot connect to a device, cannot find a required tool, or fails before the test starts.

***

## The app cannot find ADB

Make sure Android Debug Bridge is installed and available in your system PATH.

Run:

```sh
adb version
```

If the command is not found, install Android Platform Tools and restart Droid CUA after updating your PATH.

***

## Android device does not appear

Run:

```sh
adb devices
```

If the device is not listed:

* Confirm the device is connected over USB.
* Enable USB debugging on the device.
* Approve the debugging prompt on the device screen.
* Try reconnecting the cable or restarting ADB.

If the device is listed as `unauthorized`, unlock the device and approve the USB debugging prompt.

***

## Android emulator does not start

Confirm that Android Emulator CLI is installed and that the emulator can be started outside Droid CUA.

If the emulator starts manually but not from Droid CUA, restart the desktop app and select the emulator again from the device picker.

***

## iOS simulator does not appear

iOS simulator support requires macOS.

Confirm that:

* Xcode is installed.
* The simulator exists in Xcode.
* Appium is installed.
* The XCUITest driver is installed.

After installing missing tools, restart Droid CUA and open the device picker again.

***

## OpenAI API key is missing or rejected

Open **Settings** in Droid CUA and confirm that your API key is set correctly.

For CLI runs, make sure `OPENAI_API_KEY` is available in the shell or CI environment.

```sh
export OPENAI_API_KEY=your-api-key
```

Then run the test again.

***

## The test starts but the agent gets confused

This is usually not a setup problem. Improve the test input instead:

* Use the exact labels shown in the app.
* Keep the first test short.
* Add or improve `context.md`.
* Add an assertion that describes something visible on screen.
* Split long flows into smaller tests.

***

## CLI run fails before execution

Check the most common inputs:

* `--instructions` points to an existing `.dcua` file or folder.
* `--avd` matches the selected Android device, emulator, or iOS simulator.
* `--platform ios` is used for iOS simulator runs.
* `--config` points to valid JSON.
* `OPENAI_API_KEY` is available in the environment.

Run with `--debug` to create detailed artifacts for troubleshooting:

```sh
droid-cua \
  --avd adb:emulator-5554 \
  --instructions tests/login.dcua \
  --config ci/droid-cua.json \
  --debug
```
