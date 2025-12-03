# Test Flow editor

API Test flow is a series of API calls (HTTP requests) that represent **a single "user" flow you would like to test**. These requests will be executed sequentially until completion or until the first failure.

![](<../../.gitbook/assets/Screenshot (19).png>)

{% hint style="info" %}
🧠 Control visibility of the flows' list area by clicking on Flows in the Test Suite navigation panel. This way you can better focus on the flow you are currently working on.
{% endhint %}

## The Test Flow Toolbar

<figure><img src="../../.gitbook/assets/image (144).png" alt=""><figcaption></figcaption></figure>

| Option                                                                                                    | Description                                                                                                                                                                                                          |
| --------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| AutoSave <img src="../../.gitbook/assets/screen-shot-2020-11-26-at-14.20.04.png" alt="" data-size="line"> | Auto saves the test flow unless its configuration is invalid.                                                                                                                                                        |
| Login toggle                                                                                              | Toggle this switch to enable the flow to use [the Global Login](https://docs.loadmill.com/api-testing/test-suite-editor/global-login-flow) settings.                                                                 |
| CSV toggle                                                                                                | Easily re-run your test flows by using different parameters values by uploading a [CSV file](https://docs.loadmill.com/api-testing/test-suite-editor/api-tests-data-from-csv-files) containing a list of the values. |
| Flow status (default: ![](<../../.gitbook/assets/image (146).png>))                                       | Set the [status of the flow](https://docs.loadmill.com/general/api-testing1/analyzing-an-api-test-results#flow-status).                                                                                              |
| Run Flow button (![](<../../.gitbook/assets/image (145).png>))                                            | Run the edited flow as a "Trial run" to debug and validate it.                                                                                                                                                       |
| Run with overrides (![](<../../.gitbook/assets/image (147).png>))                                         | Run the edited flow as usual, but [override some parameters](https://docs.loadmill.com/test-editor/flows/flow-execution#runnning-with-overrides).                                                                    |
| Debug mode toggle (![](<../../.gitbook/assets/image (156).png>))                                          | Turn the [Debug Mode](https://docs.loadmill.com/test-editor/flows/flow-controls#debug-mode) on/off.                                                                                                                  |
| Flow scope parameters (![](<../../.gitbook/assets/image (137).png>))                                      | Set parameters which can be used in a specific flow.                                                                                                                                                                 |
| Edit flow code (![](<../../.gitbook/assets/image (138).png>))                                             | Edit the raw YAML code of the saved flow.                                                                                                                                                                            |
| Edit using AI (![](<../../.gitbook/assets/image (139).png>))                                              | Describe the desired changes and get a suggestion made by AI.                                                                                                                                                        |
| Restore deleted requests (![](<../../.gitbook/assets/image (140).png>))                                   | Allows to restore previously deleted requests (up to 10 requests), and the restoration stack clears upon refreshing the page.                                                                                        |
| Add request                                                                                               | Add en empty request to the flow                                                                                                                                                                                     |
| Paste requests                                                                                            | Paste a request - accepts CURL, and copied requests from the flow.                                                                                                                                                   |

<figure><img src="../../.gitbook/assets/image (141).png" alt=""><figcaption></figcaption></figure>

| Option                       | Description                                                                                                                                                                                |
| ---------------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| Export Flow                  | Save the flow to a YAML file. You can then import the flow into another test suite or as a load test.                                                                                      |
| Duplicate Flow               | Create a copy of the original flow within the Test Suite.                                                                                                                                  |
| Convert to Load Test         | Converts the flow to a [Load Test](test-flow-editor.md#converting-api-flow-to-load-test).                                                                                                  |
| Replace Parameter            | Replace the usage of a parameter in this flow with another parameter. (Find more information about parameters [here](https://docs.loadmill.com/api-testing/test-suite-editor/parameters)). |
| Extract Parameter            | Extract a value to a parameter from all across the test requests.                                                                                                                          |
| Copy Flow to Suite           | Copy the flow into another Test Suite.                                                                                                                                                     |
| Generate Descriptions        | Generate a suitable description to all requests in a flow using AI.                                                                                                                        |
| Configure service Definition | For GRPC, allows selecting the service that will be used in the flow.                                                                                                                      |
| Get Last Trial Run           | Open the last run's results window.                                                                                                                                                        |

### **Converting API flow to Load Test**

Easily convert an API flow to Load test by clicking on the Flow options and select "Convert to Load Test". Once you've selected ![](<../../.gitbook/assets/image (142) (1).png>), a new Load test will open containing all the requests and properties taken from the original API test.
