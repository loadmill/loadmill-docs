# TestRail integration

Loadmill & TestRail integration allows to seamlessly update TestRail test cases with Loadmill test run results.

The recommended use case is to create equivalents of your suites and tests in Loadmill (can be done via the REST API as well), then integrate the tests into your CI/CD pipeline and every time you run them, we will automatically update TestRail with the test run results. 

## Setup

**Prerequisites:** TestRail project type should be “Use multiple test suites to manage cases”.

1. In** TestRail** navigate to My Settings => API Keys - Add key - Copy it and Save Settings. 
2. Then go to Administration => Site Settings => API - check Enable API and Save Settings. 
3. In **Loadmill** navigate to Settings => Integrations => CONNECT TO TEST-RAIL.

![](<../.gitbook/assets/Screenshot (6).png>)

 4\. Fill in all the fields, test connection and click Add. That’s it, the integration setup is complete!

## How the integration works

The integration allows Loadmill to automatically create runs for matching tests in TestRail. 

The matching is based on the Test Suite and Flow (Test Case) names. It means, you need to make sure you have the same Test Suite and Test Flow names in Loadmill that you have in TestRail in order to use the integration. 

Then, when you run test flows in Loadmill, we will automatically create runs in two systems: Loadmill and TestRail hence the two systems will be in a constant sync-state. 
