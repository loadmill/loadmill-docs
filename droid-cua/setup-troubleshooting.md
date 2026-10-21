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

## Physical iPhone is not ready

On a Mac, open **Help → Run Setup Wizard → iPhone (USB)** and follow the first failed check. You can also run `droid-cua ios-device check` from the terminal.

* **Phone missing or untrusted:** reconnect the USB cable, unlock the phone, and approve **Trust**. Enable **Developer Mode** and confirm it after the phone restarts.
* **Xcode or iOS platform missing:** open the full Xcode app once and install the iOS platform under **Xcode → Settings → Components**. Command Line Tools alone are not enough.
* **Apple team or signing unavailable:** sign into Xcode with an account in a paid Apple Developer team. Confirm your Developer role and access to Certificates, Identifiers & Profiles, then choose a team if you have more than one.
* **Helper app needs setup:** use **Set up signing** or **Install helper app** in the wizard, or run `droid-cua ios-device check --fix`. If the phone asks you to trust the helper app's developer, do so under **Settings → General → VPN & Device Management**.
* **Waiting for automation or unlock:** enter the passcode on the phone when prompted. If it locks during execution, unlock it so Droid can continue.

These checks prepare UI execution. Network certificate trust is a separate setup; see [Network Capture and Assertions](network-capture.md#physical-android-or-iphone).

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
* `--avd` matches the selected Android device, emulator, iOS simulator, or `ios-device:<udid>` / `ios-device:auto` for a physical iPhone.
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
