# Composer Layout

Here's a quick walkthrough of the Loadmill Composer:

1. "Record" to start composing your test.
2. API registered in your flow. Click to expand the API to see request/response data.
3. "Analyze Test" for the AI to analyze and correlate your flow.
4. "Create Test" registers the flow in your Loadmill suite.
5. "Filter Settings" set specific URL filters.
6. Input for creating a new Loadmill suite.
7. Downloads scenario as a `.har` file.

![](<../.gitbook/assets/image (54).png>)

The composer detects all API calls sent by your application as you navigate the platform. Each API is registered with its method, URL, request body, and response.

You can click on any API to view the contents of the request registered.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FR5sLG61rPIWURKROGZgl%2Fpart_1.mp4?alt=media&token=05b05c2c-3da1-4fb6-92b5-40f4aa2f6392" %}

#### Analyzing Requests

What makes the Loadmill Composer unique is the “Analyze Requests” feature. It allows the AI to process and analyze how each request will affect your API test and what kind of parameters you need in order to make it dynamic, allowing the test to be ready for any environment.

To start correlating your flow, click “Analyze Requests”.

{% hint style="info" %}
**After creating a flow, hit “Pause”, so it does not register any incoming API calls. This will keep your API resources from being used unnecessarily.**
{% endhint %}

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2F1RCTiCJK7AGfnAI8A4SV%2Fpart_2.mp4?alt=media&token=692a1e52-de25-4f0d-b779-b7bdc6311118" %}

#### Creating Tests

Hit the “Create Test” button to upload a scenario. Loadmill generates the code for that uploaded scenario, parameterizing the correlated values in the corresponding flow.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FZCI9yADc3u6cE82KlKtd%2Fpart_3.mp4?alt=media&token=4f04d3cc-7c6e-471e-84f1-5d93fe058503" %}
