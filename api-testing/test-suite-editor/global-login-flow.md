# Global Login flow and authentication headers

Within the Login tab of each Test Suite, you can define a short flow that will run **before your test flows**. This setup flow is most commonly used to execute requests that will authenticate the test flow itself via cookies or authorization tokens. This flow can also be used to retrieve and extract data necessary for the execution of your test flows. 

Cookies received and parameters extracted by the login flow requests will be accessible by the requests of the actual test flows of that suite.

Global authentication headers configured below can use parameters extracted by the login flow requests \(In a `${param}` syntax\), and will override any matching headers in the test flow requests of that suite.

![](../../.gitbook/assets/screenshot-2021-10-03t150347.068.png)

![Global Login Flow](../../.gitbook/assets/screenshot-2021-10-03t150449.269.png)

![Global Authentication Headers](../../.gitbook/assets/screenshot-2021-10-03t150527.746.png)

You can create your login flow from scratch within the Login tab OR use a better way - create it as a [shared flow](https://docs.loadmill.com/collaboration/shared-flows) so you can re-use it in other test suites. 



