# Jira

Loadmill's Jira integration is a great way to automatically create tickets when tests fail or the expected outcome is not what was planned. You can set your own automatic ticket information directly from the Loadmill platform, making it easy to keep track of your testing progress. This integration is a great way to improve your workflow and ensure that your testing is always on track.

### Prerequisites&#x20;

Loadmill supports Jira version 5 and later versions.

### Setting up your Jira integration

#### Step 1 - Getting Jira Credentials

**Project Key**

1. Login to your Jira account.
2. Navigate to Projects > View all projects

You can see the project key on the second column after the project name.

{% hint style="info" %}
You can also create a new project and gather the project key by following the same steps above.
{% endhint %}

/video

**Jira Server URL**

The Jira server url is the origin url of your Jira account: _**https://companyname.atlassian.net**_

**API Token**

1. Navigate to Settings > Atlassian account settings.
2. Select Security on the left menu.
3. Click on <mark style="color:blue;">"Create and manage API tokens"</mark>.

/video

**Email**

The email is the account email used for your Jira account.

**Setting up Issue Types**

Many projects have their own default issue types. Make sure the issue type of your choice is created in the project.&#x20;

You can verify this by going through the following steps:

1. Navigate to Projects > View all projects.
2. Select the "Project Settings" by clicking on the 3 dots \[•••] of the project.
3. Select "Issue Types" from the left menu.

Make sure the issue type is present. You can create a new issue type by clicking on the \
"+ Add issue type" button at the end of the issue types menu.

/video

#### Step 2 - Configuring Jira on Loadmill

1. Login to your Loadmill Account
2. Navigate to Settings > Integration.
3. Select the <img src="../.gitbook/assets/connect-to-jira.png" alt="CONNECT TO JIRA" data-size="line"> integration. A window will pop up.
4. Paste all the credentials copied from Step 1.
5. Click <img src="../.gitbook/assets/connect.png" alt="connect" data-size="line">

#### Setting up Fields

Loadmill automatically sets the test description on the default fields of the issue type. You can add fields to the ticket layout by dragging and dropping the field type from the fields section to your right.&#x20;

You can also set the type of description you wish to have aside from the default ones assigned and custom your ticket message using the Loadmill dynamic variables.

The Loadmill dynamic variables are dynamic variables taken from the test run to help creating a ticket more comfortably without the copy/paste hassle.

Those variables are:

1. Test Environment: `${environment}`
2. Test Description: `${test_description}`
3. Test URL: `${test_url}`
4. Run URL: `${run_url}`
5. Failed Assertion: `${failed_assertions}`

**Quick Example**

1. Login to your Jira account and into your issue type layout.
2. Drag and drop the "Paragraph" component to the ticket layout.
3. Give a title to the "Paragraph" component and click on "Save". _<mark style="color:purple;">ex: Test Update</mark>_
4. Login to your Loadmill account > Go to Settings > Integrations > Add Jira Field.
5. Select the component name your created from step 2 and 3.
6. Give the value a description using the dynamic variables.\
   ex: Test Update on `${environment}`: `${test_description}`

Below is a more detailed example of using dynamic variables

<details>

<summary>Test Update</summary>

env: `${environment}`

test url: `${test_url}`

test run: `${run_url}`

description: `${test_description}`

</details>

#### Creating the ticket

Once your integration is complete you can now run your test cases (or use the current test runs) and open a Jira ticket based on fail criteria.

1. Select and run your test case/flow.
2. Select the failed API requests of your failed test.
3. Click on the "REPORT TO JIRA" <img src="../.gitbook/assets/report-to-jira.png" alt="report to jira" data-size="line"> button.

This will open a new tab with the ticket information with the dynamic values already set on the ticket description. You can add more information if and when you see fit and when ready click on the "Create" button at the bottom of the Jira ticket to create your ticket issue.

