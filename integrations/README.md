# Integrations

After you have built you first few meaningful tests, it's a good idea to run them automatically for every change you introduce to your application.

The best way to run API and Load tests automatically is through an external continuous integration system such as Jenkins, GitLab CI, CircleCI.

You can integrate Loadmill into your build process, by configuring it to run specific API test suite or Load tests for every build. This can be done by using the [Loadmill npm module](https://www.npmjs.com/package/loadmill) or the [Loadmill REST API](rest-api.md).

The first step for integrating Loadmill with an external system is [issuing an API token](api-tokens.md) to allow help us authenticate your external requests.

