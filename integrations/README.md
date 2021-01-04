# Integrations

After you have built your first few meaningful tests, it's a good idea to integrate them into your Continuous Delivery pipeline and start shipping faster. 

The best way to run API and Load tests automatically is through an external continuous integration system such as Jenkins, GitLab CI, CircleCI.

You can integrate Loadmill into your build process, by configuring it to **run specific API Test Suite or Load tests for every build**. This can be done by using the [Loadmill npm module](https://www.npmjs.com/package/loadmill) or the [Loadmill REST API](rest-api.md).

The first step for integrating Loadmill with an external system is [generating an API token](api-tokens.md) that allows us to authenticate your external requests.

