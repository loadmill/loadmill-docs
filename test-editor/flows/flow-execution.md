# Flow Execution

Flow Labeling is a great way to save time and improve efficiency when testing your application. By only running relevant flows, you can avoid redundant testing and focus on what's important.

In order to use Flow Labeling, you simply need to label your flows with specific keywords that identify them. You can then assign these labels to certain parts of your application's CI. When a change is made, only the relevant flows will be run.

### Assigning Labels

Testing and validation is a critical process in product and software development, but it can be tough to maintain this process with so much variety. Labeling flows is an essential part of the testing and validation process that helps developers test every aspect of their pending product.&#x20;

You may want to test multiple operations or test that your application loads correctly. Even so, every updated code to improve your application or fix a specific bug in your application passes through a categorial test scenario that doesn't include all the test cases created in your Test Suite/Plan.

Creating and assigning labels to flows is a quick and easy process with Loadmill. Simply select the flow and click on the label icon ![](../../.gitbook/assets/price-tag.png) to assign a label of your choice.

You can assign pre-made label or create a new one yourself.

The following Test Suite represents a user management application with 6 different flows. Each flow is labeled _<mark style="background-color:blue;">**"operation"**</mark>_ or _<mark style="background-color:red;">**"sanity"**</mark>_ or both.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FeLh701mEtgwoYIINX1N7%2Fflow-labeling-1.mp4?alt=media&token=d5d379ce-b22f-48b0-ae50-edd229637629" %}

{% hint style="info" %}
Make sure your flow is attached to the CI in order to run it based on labels.
{% endhint %}

### Installing Loadmill NPM Package

Before you start, install the [Loadmill NPM Package](https://www.npmjs.com/package/loadmill).

### Running Labeled Flows via CLI

Now that we've labeled our flows correctly, we'll run them according to label we pass in to the command line. We want to run all flows within a test suite that are labeled _<mark style="background-color:red;">**"sanity"**</mark>_.

Let's quickly tour what values you need before running our tests.

<table><thead><tr><th width="209">parameter</th><th width="507">where to find</th></tr></thead><tbody><tr><td><code>&#x3C;test-suite-id></code></td><td>Navigate to your test suite page and the suite id is located inside the url</td></tr><tr><td><code>&#x3C;token></code></td><td>The token is generated from the <a href="https://app.loadmill.com/app/user/settings/security">access token page</a></td></tr></tbody></table>

Open your CLI and run the following command:&#x20;

```
loadmill <test-suite-id> --test-suite -w -t <token> --labels --report "label1,label2"
```

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FKX7tJkrUbBj7ugas1cpa%2Fflow-labeling-cli.mp4?alt=media&token=f2ce0b13-5593-4a2f-8bd1-abde87ceed6a" %}

To conclude, flow labels allow us to focus our tests based on our needs regardless of the amount of test cases we have on our test suites or test plans. We could schedule daily test runs on _<mark style="background-color:red;">**"sanity"**</mark>_ labeled flows and run "operation" flows for every time we push an update to our code.
