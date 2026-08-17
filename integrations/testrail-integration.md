# TestRail integration

Loadmill & TestRail integration allows to seamlessly update TestRail test cases with Loadmill test run results.

The recommended use case is to create equivalents of your suites and tests in Loadmill (can be done via the REST API as well), then integrate the tests into your CI/CD pipeline and every time you run them, we will automatically update TestRail with the test run results.&#x20;

## Setup

**Prerequisites:** TestRail project type should be “Use multiple test suites to manage cases”.

1. In **TestRail** navigate to My Settings => API Keys - Add key - Copy it and Save Settings.&#x20;
2. Then go to Administration => Site Settings => API - check Enable API and Save Settings.&#x20;
3. In **Loadmill** navigate to Settings => Integrations => CONNECT TO TEST-RAIL.

![](<../.gitbook/assets/Screenshot (6).png>)

&#x20;4\. Fill in all the fields, test connection and click Add. The integration setup is complete :)&#x20;

🧙‍♂️ Feel free to enable the automatic test creation option so that Loadmill will automatically create missing Test Suites and Test Cases in TestRail.

![](<../.gitbook/assets/Screenshot (68).png>)

## How the integration works

The integration allows Loadmill to automatically create runs for matching tests in TestRail.&#x20;

By default, the matching is based on the Test Suite and Flow (Test Case) names. It means, you need to make sure you have the same Test Suite and Test Flow names in Loadmill that you have in TestRail in order to use the integration.&#x20;

Then, when you run test flows in Loadmill, we will automatically create runs in two systems: Loadmill and TestRail hence the two systems will be in a constant sync-state.&#x20;

In case, you are going to change names in TestRail or Loadmill so would like to do matching per id, you can enter test flows - click on <img src="../.gitbook/assets/Screenshot (69).png" alt="" data-size="line"> and choose the test case you would like to always be attached to this test flow.&#x20;

![](<../.gitbook/assets/Screenshot (70).png>)

From now on, the integration will work per the pairing by id only. You will always be available to detach flows from test cases if needed.&#x20;
