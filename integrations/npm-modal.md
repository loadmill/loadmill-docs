# CI integration

The easiest way to integrate your API tests into your CI/CD pipeline is by using **** [**our npm module**](https://www.npmjs.com/package/loadmill).&#x20;

### How it works

1. Install the npm module as described [here](https://www.npmjs.com/package/loadmill). Make sure you have node.js version 14 or higher installed on your machine.
2. Create an API token that will be used for the integration. To generate it, navigate to Settings - [Security](https://www.loadmill.com/app/user/settings/security).
3. Create a Test Plan and include into it all Test Suites you would like to run in the CI. Read more about Test Plans [here](https://docs.loadmill.com/api-testing/test-plan).
4.  Initiate execution of the Test Plan by running command:

    ```
    loadmill  <test-plan-id> --test-plan -w -v -t <token> --report --colors

     // Take the <test-plan-id> parameter value from its URL going after /api-tests/test-plans/. 
    ```

Other supported options can be found [here](https://www.npmjs.com/package/loadmill).

### Docker Image&#x20;

You can also use Dockerfile attached to run the Test Plan you wish:

{% file src="../.gitbook/assets/Dockerfile" %}

To build it use this command : `docker build -t loadmill-runner .`

To run it use this command: `docker run -it --env TP_ID=3085de2f-bc42-4727-9c4b-ab649ca4a285 --env TOKEN=<api token> --env BUILD_NUMBER=<the build number> loadmill-runner`

