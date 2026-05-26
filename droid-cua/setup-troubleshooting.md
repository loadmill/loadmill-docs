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

## Web browser is not found

For web tests, install Google Chrome or Microsoft Edge and restart Droid CUA.

For CLI runs, confirm the selected browser is supported:

```sh
droid-cua --target web --browser chrome --instructions tests/search.dcua
```

Use `--browser edge` if you want to run against Microsoft Edge.

***

## LambdaTest cloud device run fails before connecting

Check that the required LambdaTest inputs are set:

* `LAMBDATEST_USERNAME`
* `LAMBDATEST_ACCESS_KEY`
* `--device-source lambdatest`
* `--platform android` or `--platform ios`
* `--device-name`
* `--os-version`
* `--app`
* `--instructions`

Android cloud runs require an `.apk` file. iOS cloud runs require an `.ipa` file.

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
* `--target web` is used for browser runs.
* `--config` points to valid JSON.

Run with `--debug` to create detailed artifacts for troubleshooting:

```sh
droid-cua \
  --avd adb:emulator-5554 \
  --instructions tests/login.dcua \
  --config ci/droid-cua.json \
  --debug
```
