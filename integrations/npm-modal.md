# npm Module

The [Loadmill npm module](https://www.npmjs.com/package/loadmill) allows users to:

1. Run API tests on loadmill.com.
2. Run Load tests on loadmill.com.
3. Do both programmatically or via [CLI](https://www.npmjs.com/package/loadmill#cli).

The easiest way **to integrate your API tests into your CI/CD pipeline is by using the npm module**. How it works:

1. Install the npm module as described [here](https://www.npmjs.com/package/loadmill). 
2. Create an API token that will be used for the integration. To generate it, navigate to Settings - [Security](https://www.loadmill.com/app/user/settings/security). 
3. Create a Test Plan and include into it all Test Suites you would like to run in CI/CD. Find more information about Test Plans [here](https://docs.loadmill.com/api-testing/test-plan). 
4. Initiate execution of the Test Plan by running command: 

   ```text
   loadmill  <test-plan-id> --test-plan -w -v -t <token> --report --colors

    // Take the <test-plan-id> parameter value from its URL going after /api-tests/test-plans/. 
   ```

Other supported options can be found [here](https://www.npmjs.com/package/loadmill). 

