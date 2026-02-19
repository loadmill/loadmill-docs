# Test Plan

A Test Plan is a collection of Test Suites that belong to specific tasks or features or have another reason to be run together. In general, the primary use of Test Plans is running several Test Suites integrated into your Continuous Delivery pipeline, although you may still run it manually in the UI.

The image below shows the Test Plan hierarchy in Loadmill.

![](<../../.gitbook/assets/Screenshot (27).png>)

![](<../../.gitbook/assets/Screenshot (28).png>)

![](../../.gitbook/assets/screen-shot-2021-01-19-at-17.26.24.png)

### Creating and running a Test Plan

Let's create and run your first Test Plan together:

1. Navigate to the Test Plans tab and click on the NEW TEST PLAN button.
2. Let's look at the Test Plan editor page.

![](<../../.gitbook/assets/Screenshot (29).png>)

3\. Click on MANAGE SUITES to add Test Suites to the Test Plan. You can pick specific Test Suites or all by clicking ALL SUITES. Once the Test Suites are selected, click CLOSE.

{% hint style="warning" %}
:brain: Make sure the Test Suites you would like to run within the Test Plan have test flows with CI toggle on. Otherwise, the Test Suites will be grayed out and won't run.
{% endhint %}

![](../../.gitbook/assets/screenshot-2021-04-05t112455.593.png)

4\. Now you have two options:

* Run the Test Plan by clicking RUN TEST PLAN.
* Use the RUN BY LABELS option to select relevant labels and then click RUN TEST PLAN so that only Test Suites whose test flows have specific labels will run.

![](../../.gitbook/assets/ezgif.com-gif-maker-26-.gif)

### Test Plan navigation bar

The navigation bar allows:

1. To set Test Suites to run in parallel (up to 12) so you will be able to significantly save running time.
2. To select a GitHub repository branch to take Test Suite data from while using [the GitHub integration](https://docs.loadmill.com/integrations/github-integration/data-sync-connection-to-github#running-test-plan-with-the-data-committed-to-github).
3. To configure Test Plan parameters values so that the Test Plan run will take these values in **all the Test Suites using the parameters**.

![](<../../.gitbook/assets/Screenshot (30).png>)

&#x20;    4\. To define a **Setup Flow** that will run before all suites of the Test Plan. The Setup Flow common use cases: creation of an account, user, env cleanup and any other action/s you need to perform before running the Test Plan suites. You can either create the flow from scratch in the Setup Flow tab or use a [shared flow](https://docs.loadmill.com/collaboration/shared-flows) by clicking on USE A SHARED FLOW.

![](<../../.gitbook/assets/Screenshot - 2022-02-08T150241.243.png>)

&#x20;   5\. Set Test Plan [notifications](#notifications) so that you will get email/slack notifications with all the Test Suites' information.

![](<../../.gitbook/assets/Screenshot (32).png>)

&#x20;   6\. To schedule the Test Plan to run periodically to constantly validate your application status.

![](<../../.gitbook/assets/Screenshot (33).png>)

### Notifications

You can configure Test Plan notifications to get a summary with all the Test Suites' information once a Test Plan run is complete. Notifications can be set from the Test Plan navigation bar.

#### Email

Enter one or more email addresses to receive a notification email after each Test Plan run. The email includes the overall run status and a breakdown of each Test Suite's result, making it easy to review failures without opening the Loadmill UI.

#### Slack

Select a Slack channel (or enter a channel ID) to receive notifications when a Test Plan run ends. For each channel you can configure:

- **For** — which runs trigger a notification (e.g. all runs, failures only).
- **Notification content** — a standard report with options to set how failures are reported (by flows or suites), the detail level, users to tag, and an optional custom message.

**AI-powered failure analysis**

Instead of a standard report, you can opt for an AI summary. Loadmill will analyze all failures in the run and send a single Slack message explaining the root cause, giving your team an instant, actionable diagnosis without having to dig through individual flow results.

![](../../assets/ai-tpr-ef.png)

### Integrating Test Plan into CI/CD

To integrate Test Plans into your Continuous Delivery pipeline, use our npm module. See an example of how to launch a Test Plan below:

```
loadmill --test-plan <test-plan-id> -w -v -t <token> --report --colors
```

Find more examples and supported CLI options [here](https://www.npmjs.com/package/loadmill).

### Analyzing Test Plan results

After running the Test Plan, you will be redirected to the Test Plan Run page. The Test Plan Run report page shows the list of executed Test Suites as defined in the Test Plan. The Test Suites table shows **each suite's description, the number of its flows, duration, and status**. Use the table filter to filter the Test Suites by their status.

![](../../.gitbook/assets/screenshot-2021-03-10t095854.448.png)

You can easily re-run Test Plan by clicking **RE-RUN** or **Run only Failed Suites**.
