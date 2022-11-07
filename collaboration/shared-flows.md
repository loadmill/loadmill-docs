# Shared Flows

The **Shared Flows** feature allows users to re-use test flows in different Test Suites and Test Plans.

The common use case for Shared Flows is when you have several login test flows. For example, the email/password login that should be used in some Test Suites and the login via a social media platform that should be used in others. To configure this in Loadmill:

* Navigate to **Shared Flows.**

![](<../../.gitbook/assets/Screenshot (39).png>)

* Click on the "+ NEW SHARED FLOW" button if you would like to create a login flow from scratch OR "IMPORT SHARED FLOW" in case you already have it in JSON format.
* We recommend using the "DRY RUN" option first to test your flow and then Publish it.
* Now you can go to the Test Suite where you would like to use it => the Login tab => click CHANGE LOGIN FLOW SOURCE and select your shared flow.

![](<../../.gitbook/assets/Screenshot (41).png>)

Thus, the shared flow will run before every test flow where the Login checkbox is checked.

Then, you can always track which Test Suites using your Shared Flows.

![](<../../.gitbook/assets/Screenshot (40).png>)

The COLLABORATORS tab allows to manage access to the shared flow so that only specific team members will be able to edit it.

![](<../../.gitbook/assets/Screenshot (100).png>)

By the way, you can also use shared flows to define [Before & After](https://docs.loadmill.com/api-testing/test-suite-editor/before-and-after-hooks) hooks and [Setup Flow](https://docs.loadmill.com/api-testing/test-plan#test-plan-navigation-panel).
