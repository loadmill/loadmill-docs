# Jira

Loadmill Jira integration allows you to automatically create Jira tickets when tests fail or that the expected outcome is not what was planned. You can set your own automatic ticket information streight from the Loadmill platform.

### Prerequisites&#x20;

Loadmill supports Jira version 5 and later versions.

### Setting up your Jira integration

#### Step 1 - Getting Jira Credentials

**Project Key**

1. Login to your Jira account and create a new project or use an existing project.
2. Chose any type of project or project templates.
3. Name your project.
4. Navigate to Projects > View all projects

You can see the project key on the second column after the project name.

/video

**Jira Server URL**

The Jira server url is the origin url of your Jira account: https://companyname.atlassian.net

**API Token**

1. Navigate to Settings > Atlassian account settings
2. Select Security on the left menu
3. Click on "Create and manage API tokens"
4. Create an API token.

/video

**Email**

The email is the account email used to create/login your Jira account.

**Setting up Issue Types**

Many projects have their own default issue types. Make sure the issue type of your choice is created in the project.&#x20;

You can verify this by going through the following steps:

1. Navigate to Projects > View all projects.
2. Select the "Project Settings" by clicking on the 3 dots of the project.
3. Select "Issue Types" from the left menu.

Make sure the issue type of your choice is present. You can create a new issue type by clicking on the "Add issue type" button at the end of the issue types menu.

/video

#### Step 2 - Configuring Jira on Loadmill

1. Login to your Loadmill Account
2. Navigate to Settings > Integration.
3. Select the "CONNECT TO JIRA" integration. A window will pop up.
4. Paste all the credentials copied from Step 1.
5. Click "CONNECT"

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

Once thats complete any failed test will have the "Report To Jira" button next to the failed API request. Clicking the button will open a new Create Ticket Jira tab with all it's dynamic values from the test run assigned. You can manually add more information if you see fit and when ready, click on the "Create" button to create your Jira ticket.

