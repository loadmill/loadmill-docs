# XRay

Xray is a powerful test management tool that enables you to manage your testing process more effectively. With Xray, you can create and track tests, assign them to specific team members, and view results in real-time.&#x20;

Now, users can automatically sync their Loadmill tests with its new Xray integration, making it easier than ever to keep track of API performance and ensure that all tests are up-to-date.

With this integration, users will be able to:

* Automatically sync Loadmill tests with Xray projects.
* View Loadmill test results directly in Xray.
* Easily share Loadmill test results with stakeholders.

### Prerequisites

1. Make sure that **"Test"** and and **"Test Execution"** issue types are present in your project.
2. Create an Xray API key token.

{% hint style="info" %}
1. Go to **Project Settings > Apps > Xray Settings > Summary** to verify of the issue types are present within your project.
2. Go to **Apps > Manage your apps > under the Xray section > API Keys** to create an API key.
{% endhint %}

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FFFvp5o0RB1CDM6BLlgwm%2Fxray-integration-prerequisites.mp4?alt=media&token=75afff93-772b-445f-9ddf-4688d6122097" %}

### Xray Integration Setup

1. Go to Loadmill > Settings > Integrations > "CONNECT TO XRAY"
2. Insert the required credentials.
3. Click "CONNECT"

#### Credentials

**Project Key:** Go to **Jira > Projects > View all projects** and select the key from the project table.\
**Client Id:** Go to **Jira > Apps > Manage your apps >  Xray section > API Keys** and copy the client id\
**Client Secret:** Go to **Jira > Apps > Manage your apps >  Xray section > API Keys** and copy the client secret.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FMD6w5SDatyCwwWLAFRNH%2Fxray-integration-setup.mp4?alt=media&token=fed7f0ce-f9af-43ad-964a-2ffcb1d141a3" %}

### Pairing to Xray

You can pair your entire Test Suite with Xray. Pairing your Test Suite sets up a new "Test" ticket for each flow and connects to it accordingly. Running the paired Test Suite creates a "Test Execution" ticket with reported flow statuses and updates each connected "Test" flow ticket with its flow status.&#x20;

{% hint style="warning" %}
To enable Test Suite Pairing you need to enable CI for the desired flow. This is an essential step as it automates Xray reports on run.
{% endhint %}

You can pair each Loadmill test flow individually with Xray. Each paired flow updates Xray tests upon each Test Suite run.&#x20;

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FmGCMWjY4N1Ck6CoEHLEN%2Fxray-integration-pairing.mp4?alt=media&token=ebbe5f7d-d256-485b-9724-ff327c44ecd0" %}

{% hint style="info" %}
Having your CI connected to Loadmill allows you to automate your workflow lets you focus on your products infrastructure while your tests are ran and reported for each push requests created.
{% endhint %}

### Running Test Plan with Xray

To run your Test Plan with Xray simply click on the "Run with Xray Test Execution" from the "Run Test Plan" dropdown and select. Running your Test Plan updates the connected flow to the Xray test results accordingly.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2F344mDNzlfGVohezt7vni%2Fxray-integration-test-plan.mp4?alt=media&token=81c16109-2ac6-4290-ac11-ab9a83caf9e0" %}

### Xray Test Results

Each Test Suite Run creates a new "Test Execution" ticket containing reported test flows and their run statuses.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2Fv04rFnYG6TkpA7y8TRlh%2Fxray-integration-running.mp4?alt=media&token=d71eb3a7-45af-4e03-a5df-4948c7bf6c62" %}
