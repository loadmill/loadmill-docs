# Flow Execution

### Running with Overrides

When running a flow within the flow editor for debugging purposes, it can be very convenient to replace certain parameters for a single run. Instead of changing the parameter value in the global parameters window, you can simply click the 'run with overrides' button (![](<../../.gitbook/assets/image (148).png>)), and then set values for a specific execution. This won't affect the global parameters, providing a quick and simple way to debug your flows. i.e.:

This is the global parameter: ![](<../../.gitbook/assets/image (151).png>), and we want to check something specific and change the value of `email` for only one run. We'll use the 'run with overrides' button to execute it and reset its value. For example:

<figure><img src="../../.gitbook/assets/image (155).png" alt=""><figcaption><p>Good to know: the override parameters in this window are saved for subsequent 'runs with overrides' as well.</p></figcaption></figure>

### Assigning Labels

Flow Labeling is an efficient way to save time and enhance productivity during application testing. By executing only relevant flows, you can avoid redundant testing and concentrate on critical aspects.

To utilize Flow Labeling, simply label your flows with specific keywords for identification. Then, assign these labels to relevant sections of your application's CI. This ensures that only relevant flows are executed when changes are made.

Testing and validation are crucial in product and software development, but maintaining this process amidst diverse requirements can be challenging. Flow labeling is essential for developers to effectively test every aspect of their product.

You may need to test multiple operations or ensure your application loads correctly. However, each update or bug fix undergoes a categorical test scenario that may not encompass all test cases from your Test Suite/Plan.

Creating and assigning labels to flows is a straightforward process with Loadmill. Just select the flow and click on the label icon ![](../../.gitbook/assets/price-tag.png) to assign a label of your choice. You can either assign a pre-made label or create a new one yourself.

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
