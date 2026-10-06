# Using Secrets

Use a `.secrets` file for passwords and other sensitive values that Droid needs to enter into the app under test. Your tests refer to the values by name, so you can share the same test with teammates and run it in different environments without putting credentials in the test itself.

This works for mobile and web tests, including Design Mode and CLI runs.

## Create the file

Create a file named `.secrets` in your Droid project folder, alongside `context.md` and your tests:

```text
tests/droid/
├── context.md
├── login.dcua
└── .secrets
```

Use one `KEY=value` entry per line. For example:

```dotenv
USER_EMAIL=tester@example.com
USER_PASSWORD="replace-with-your-test-password"
```

Replace these example values with the credentials for your test account. Choose clear key names that explain their purpose. You can use quotes around values and add comments on lines beginning with `#`.

## Refer to secrets in your test

Use the key names in the instructions rather than the actual values:

```text
Open the sign-in screen.
Enter USER_EMAIL in the email field using the secret.
Enter USER_PASSWORD in the password field using the secret.
Sign in and verify the Accounts screen is visible.
```

Droid tells the agent which secret keys are available. When the agent requests a value by key, Droid resolves it and types it into the selected field. The secret-typing action passes the key to the AI model instead of the value.

In Design Mode, you can likewise ask Droid to sign in using `USER_EMAIL` and `USER_PASSWORD`. Keep the values out of the design instructions, `.dcua` tests, `context.md`, and `test-data.md`.

## Where Droid loads secrets

In the desktop app, execution and Design Mode load `.secrets` from the selected project's root folder. Tests in nested folders use that same file.

The CLI loads `.secrets` from the current working directory, even when `--instructions` points to a test elsewhere. To use the file in the example project above, run the command from that folder:

```sh
cd tests/droid
droid-cua --avd adb:emulator-5554 --instructions login.dcua
```

If Droid reports that a secret key is missing, check the file location and spelling of the key. The key in the test must match the key in `.secrets`, including capitalization.

## Use secrets in CI

Store credentials in your CI system's secret store. You can make a `.secrets` file available in the job's working directory or supply values with `--secrets`:

```sh
droid-cua \
  --avd adb:emulator-5554 \
  --instructions login.dcua \
  --secrets "USER_EMAIL=${DROID_USER_EMAIL},USER_PASSWORD=${DROID_USER_PASSWORD}"
```

Here, `DROID_USER_EMAIL` and `DROID_USER_PASSWORD` are environment variables supplied by your CI secret store. Environment variables alone do not become Droid typing secrets; pass them through `.secrets` or `--secrets`.

The flag accepts comma-separated `KEY=value` pairs. Values supplied by the flag override matching keys in `.secrets` for that run. Use the file for values containing commas. See [Running Droid Tests in CI](ci.md) for device and pipeline setup.

## Keep credentials out of shared files

`.secrets` is a plain-text local file. Keep it out of version control, along with `.env`. Add these entries to your repository's `.gitignore`:

```gitignore
.secrets
.env
```

You can commit a `.secrets.example` file containing key names and placeholder values to help teammates set up their own credentials.

`.secrets` holds values Droid enters into the tested application. `.env` holds credentials Droid itself needs, such as Loadmill or AI-provider access. Putting a password in `.env` does not make it available as a typing secret.

Droid's secret-typing action records the key instead of the resolved value in logs and reports. Screenshots are not masked: if the application displays a value, it can appear in screenshots sent to the model or saved in a report. Use test accounts and review screenshots before sharing results.
