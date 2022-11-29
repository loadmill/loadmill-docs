# TestRail

Loadmill now integrates with TestRail, a comprehensive, test management product that enables you to create and sync test suites, plans and their related data in one place.

### Getting Started

#### Creating/setting a project

1. Login to your TestRail account.
2. Create a new project. _`ex: loadmilldocs`_
3. Make sure you select "Use multiple test suites to manage cases" when creating your project.

You can also change your current project settings by going to \
Administration > Project > Select your project > Edit

{% hint style="info" %}
Selecting "Use multiple test suites to manage cases" when creating your project is essential for your integration as Loadmill applies the same structure to create and update test suites.
{% endhint %}

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F2vjiLjsWmvQaVMxaG2Eb%2Fuploads%2F42FHU34fiSQqS7sOUZrO%2Ftestrail-creating-project.mp4?alt=media&token=6f08c58c-4d04-4116-92b6-b73981a720a4" %}

#### Generating API Key

1. Go to Administration > Site Settings > API > Check the "Enable API" checkbox > Click on "Save Settings"
2. Go to your user name (top-right) > My Settings > API Keys.
   1. Click on Add key.
   2. Name your API key.
   3. Click on "+ Generate Key".
   4. Copy the generated API key.
   5. Click on "+ Add Key".
   6. Click on Save Settings afterwards.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F2vjiLjsWmvQaVMxaG2Eb%2Fuploads%2FAT6pxDPwX7wQZ2DXLlPI%2Ftestrail-integration-setup.mp4?alt=media&token=cbab18c2-1dd7-4af5-ba28-3d9e0f5df412" %}

### Integration Setup

1. Navigate to your Loadmill account > Settings > Inetgrations > Click on <img src="broken-reference" alt="connect to testrail" data-size="line">.
2. _Description_ (optional) - you can name it loadmill-integration.
3. _Domain_ - domain of the account (_`ex: https://organization.testrail.io`_).
4. _Username_ - same as your email used to sign up to TestRail with.
5. _Token_ - copied token from the "Generating API Key" steps.
6. _Project_ - name of the project you created.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F2vjiLjsWmvQaVMxaG2Eb%2Fuploads%2FdruM37vqMEeSc8LJ9MDI%2Ftestrail-integration-setup-loadmill.mp4?alt=media&token=81c7e81c-ab93-4a6b-8de7-6baa455779fa" %}

### Pairing your Test Suite

You can pair your Loadmill suite to an existing TestRail suite or have Loadmill create a new TestRail Test Suite every time you pair your Loadmill suite. Every test runs will automatically report to the TestRail suite the Loadmill suite is assigned to.

{% hint style="warning" %}
To enable Test Suite Pairing you need to enable CI for the desired flow. This is an essential step as it automates Xray reports on run.
{% endhint %}

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F2vjiLjsWmvQaVMxaG2Eb%2Fuploads%2FkVOEuhKtLSLw8K5flbu7%2Ftestrail-pairing-suites.mp4?alt=media&token=46358c21-8f27-4a72-b1f9-df29ddf3fe44" %}

### TestRail Results

Running your test case will trigger a TestRail Test Run report on the selected TestRail suite. You can view your TestRail report to keep track of the data and test runs. This is an exciting way to ensure that your tests are being run as planned and that you're getting the most accurate results possible.

You can access your TestRail results from the Loadmill Test Run results and vice versa. Simply open the "Configuration" of your Loadmill Test Run and click on the TestRail Suite ID to access your TestRail results. From TestRail, select the Test Runs & Results tab > Open a Test Run and click on the link from the run description.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F2vjiLjsWmvQaVMxaG2Eb%2Fuploads%2FLEKVBKLeP7MGjwvn9rZA%2Ftestrail-running-suite.mp4?alt=media&token=76e25875-f6bf-4fcd-9768-9c6d7195ff75" %}

### Loadmill and TestRail Test Plans

You can also connect a Loadmill Test Plan with a TestRail Test Plan:

1. Go to your project > Test Runs & Results tab > + Add Test Plan (on your right)
2. Setup your TestRail Test Plan name and information if necessary.
3. Click on ✓ Add Test Plan.
4. Go to your Loadmill account > Select a Test Plan of your choice
5. Select the dropdown arrow from the Run Test Plan button.
6. Click on "Run with TestRail Plan".
7. Select a test plan from the dropdown.
8. Click on "Run Test Plan"

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F2vjiLjsWmvQaVMxaG2Eb%2Fuploads%2FZPFTkawu76pxKhisdCk4%2Ftestrail-rtest-plan.mp4?alt=media&token=828f153e-230f-4ce3-bd99-4006c1c3b5f3" %}

{% hint style="info" %}
You can skip steps from 1 to 3 if you already have a Test Plan configured on TestRail
{% endhint %}

