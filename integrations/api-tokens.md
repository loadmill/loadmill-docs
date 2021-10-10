# API Tokens

In order to use the [Loadmill npm module](https://www.npmjs.com/package/loadmill) or the [Loadmill REST API](rest-api.md), you will need to generate an **API Token**.

## Generating a Token

1. Navigate to **the user's Avatar** > **Settings** > [**Security**](https://www.loadmill.com/app/user/settings/security)**.**

![](../.gitbook/assets/screenshot-2021-06-13t094954.242.png)

    2\. Enter a description for the token's intended usage and click **GENERATE**.

You will be given an arbitrary string of characters that will be shown to you ONLY ONCE - this is your API token, make sure to copy and store it in a safe place.

## Using a Token

Tokens may be used in one of three ways:

1. Passed in the options object to the [Loadmill npm module](https://www.npmjs.com/package/loadmill), e.g. `require('loadmill')({token: "ewszIIzEDIeORLwTSrcEvrKKEWQeR9yzQqyCCKlK"})`
2. Given as a **basic authentication** username with a blank password, e.g. `https://ewszIIzEDIeORLwTSrcEvrKKEWQeR9yzQqyCCKlK@www.loadmill.com/api/tests`
3. Given in an **Authorization** HTTP header as a bearer token, e.g. `Authorization: Bearer ewszIIzEDIeORLwTSrcEvrKKEWQeR9yzQqyCCKlK`

## Protecting Tokens

An API token enables its bearer to create and run load tests within your account. You can do almost anything you can do in our web interface using tokens, except changing your password, making payments and generating more tokens.

Therefore, you should keep your token as safe as you can from untrusted third parties. If you suspect it may have been compromised, you may revoke the token via **Settings** > [**Security**](https://www.loadmill.com/app/user/settings/security) and generate a new one.
