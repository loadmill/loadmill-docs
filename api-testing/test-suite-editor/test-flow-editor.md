# Test Flow editor

API Test flow is a series of API calls \(HTTP requests\) that represent **a single "user" flow you would like to test**. These requests will be executed sequentially until completion or until the first failure.

![](../../.gitbook/assets/screenshot-2021-10-03t132024.726.png)

## The Test Flow toolbar

![](../../.gitbook/assets/screenshot-2021-10-03t132126.564.png)

| Option | Description |
| :--- | :--- |
| Run Flow button \(▶\) | Run the edited flow as a "Trial run" to debug and validate it. |
| Import CSV                | Easily re-run your test flows by using different parameters values by uploading a [CSV file](https://docs.loadmill.com/api-testing/test-suite-editor/api-tests-data-from-csv-files) containing a list of the values. |
| Login toggle | Toggle this switch to enable the flow to use [the Global Login](https://docs.loadmill.com/api-testing/test-suite-editor/global-login-flow) settings. |
| CI toggle            | Toggle this switch to enable the flow to run when executed from your continuous integration pipeline. You can use [our npm module](https://docs.loadmill.com/integrations/npm-modal) to execute a Test Suite to test every build in CI. |
| AutoSave                         ![](../../.gitbook/assets/screen-shot-2020-11-26-at-14.20.04.png) | Auto saves the test flow unless its configuration is invalid. |
| Export Flow | Save the flow to a `.JSON` file. You can then import the flow into another test suite or as a load test. |
| Duplicate Flow | Create a copy of the original flow within the Test Suite. |
| Delete Flow | Delete the flow. |
| Set As Login Flow | Copy the full flow to [the Login tab](https://docs.loadmill.com/api-testing/test-suite-editor/global-login-flow).  |
| Replace     Parameter | Replace the usage of a parameter in this flow with another parameter. \(Find more information about parameters [here](https://docs.loadmill.com/api-testing/test-suite-editor/parameters)\). |
| Extract Parameter | Extract a value to a parameter from all across the test requests. |
| Copy flow to suite | Copy the flow into another Test Suite. |

## Other flow controllers

### **Add Request button**

Add new requests to a flow. Once added you can drag a request to change its order by grabbing it at the top right corner. 

### **Converting API flow to Load Test**

Easily convert an API flow to Load test by clicking on the Flow options menu ![](../../.gitbook/assets/screen-shot-2020-02-03-at-12.12.19-pm.png) located on the top right and select "Convert to Load Test". Once you've selected "Convert to Load Test", a new Load test will open containing all the requests and properties taken from the original API test.

![](../../.gitbook/assets/screenshot-2021-07-05t104357.068.png)

![](../../.gitbook/assets/screenshot-2021-07-05t104522.112.png)

### Skip and Stop Condition

Set a skip or stop condition between requests. Let's say you would like to skip "Purchase" Request if the preceding "Get Price" Request response returns a price above the current budget. This could be accomplished by extracting price and budget to [parameters](https://docs.loadmill.com/api-testing/test-suite-editor/set-parameters-extractions) and setting the Purchase Request skip condition to ${budget &lt;= price}.

![](../../.gitbook/assets/screenshot-2021-10-03t132644.977.png)

![](../../.gitbook/assets/screenshot-2021-10-03t132710.663.png)



