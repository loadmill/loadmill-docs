# Shared Flows

The **Shared Flows** feature allows users to re-use test flows in different Test Suites and Test Plans. 

The common use case for Shared Flows is when you have one or several login test flows. For example, the email/password login that should be used in some Test Suites and the login via a social media platform that should be used in others. To configure this in Loadmill:

* Navigate to **API TESTS =&gt; Shared Flows \(visible to Team Admins only\)**

![the Shared Flows tab](../.gitbook/assets/screen-shot-2020-11-17-at-12.59.49-pm.png)

* Click on the "+ NEW SHARED FLOW" button if you would like to create a login flow from scratch OR "IMPORT SHARED FLOW" in case you already have it in JSON format.
* We recommend using the "DRY RUN" option first to test your flow and then Publish it. 
* Now you can go to the Test Suite where you would like to use it =&gt; the Login tab =&gt; click CHANGE LOGIN FLOW SOURCE and select your shared flow. 

![](../.gitbook/assets/screenshot-50-.png)

Thus, the shared flow will run before every test flow where the Login checkbox is checked. 

Then, you can always track which Test Suites using your Shared Flows. 

![](../.gitbook/assets/screenshot-2021-02-11t152411.061.png)

By the way, you can also use shared flows to define [Before & After](https://docs.loadmill.com/api-testing/test-suite-editor/before-and-after-hooks) hooks and [Setup Flow](https://docs.loadmill.com/api-testing/test-plan#test-plan-navigation-panel). 

