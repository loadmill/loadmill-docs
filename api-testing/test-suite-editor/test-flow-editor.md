# Test Flow editor

API Test flow is a series of API calls \(HTTP requests\) that represent a single "user" flow we would like to test. These requests will be executed sequentially until completion or until the first failure.

![Test Flow editor section](../../.gitbook/assets/testsute_flow.png)

### The Test Flow toolbar

![](../../.gitbook/assets/image%20%2812%29.png)

#### **Run Flow button** \(▶\)

Run the edited flow as a "Dry run" to debug and validate it.

#### **Export Flow**

Save the flow to a `.JSON` file. You can then import the flow into another test suite or as a load test.

#### **Replace parameter**

Replace the usage of a parameter in this flow with another parameter \(Parameters will be discussed later in depth\) 

#### **CI toggle**

Toggle this switch to enable the flow to run when executed from your continuous integration pipeline. You can use our NPM module to execute a Test Suite to test every build in CI, this will be explained lated in the Integrations section.

### Other flow controllers

#### **Add Request button**

Add new requests to a flow. Once added you can drag a request to change its order by grabbing it at the top right corner. 

**Converting an API flow to a Load test**

Easily convert an API flow to Load test by clicking on the Flow options menu ![](../../.gitbook/assets/screen-shot-2020-02-03-at-12.12.19-pm.png) located on the top right and select " "Convert to Load Test". Once you've selected "Convert to Load Test", a new Load test will open containing all the requests and properties taken from the original API test.

![Select &quot;Convert To Load Test&quot; in the flow&apos;s options menu](../../.gitbook/assets/assets_-lhdbundi3wpd9vsolzu_-m-9ve8pnpzqxg6k-l5h_-m-9yr0z6kwxn_zozw4h_screen-shot-2020-02-03-at-12.16.25-pm.png)

![The newly created Load Test from the API flow](../../.gitbook/assets/screen-shot-2020-02-03-at-12.16.40-pm.png)

