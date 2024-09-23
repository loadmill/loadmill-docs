---
description: >-
  Configure real-time notifications to reach any Slack channel/s you wish in
  just a few clicks.
---

# Slack integration

Slack has more than 12 million daily active users and 156,000 organizations subscribe to the app so it's become essential to get notified about important events via Slack. We introduce our **Loadmill app on Slack** that allows to send notifications per API Test, Load Test, Test Plan run to the Slack channel you wish. Follow the steps below to configure the integration.

1. Navigate to Settings => Integrations. Click CONNECT TO SLACK.

![](<../.gitbook/assets/Screenshot (45).png>)

&#x20;2\. You will be redirected to the page where you need to click **Allow** in order to give relevant permissions to the Loadmill app.

3\. You are almost set, the only thing is left to do is to choose what notifications you would like to get and in which channel. To do that, go to Notifications (the tab above Integrations) => ADD NOTIFICATION => Notification type: Slack => choose channel => select relevant test type and status.

&#x20;🧠 Tip: the most popular notifications are about Failed Test Plan Runs :)&#x20;

![](<../.gitbook/assets/Screenshot 2024-09-23 at 13.12.03.png>)

That's it, you did it! 🎉 From now on, you won't miss any important Loadmill event.

![Loadmill notification in Slack](../.gitbook/assets/screen-shot-2021-07-14-at-12.16.21.png)

### Retrieving a Slack Channel ID

Occasionally, due to limitations with the Slack API, Loadmill may be unable to automatically retrieve the Slack channel ID. When this occurs, we will need the user  to provide the channel ID manually.

To find the channel ID:

1. Open the Slack channel where you would like Loadmill to send notifications.
2. Click on the channel name to open the **channel details**.
3. Scroll down and click the copy icon next to the channel ID.

<figure><img src="../.gitbook/assets/channel-id-explanation.gif" alt=""><figcaption></figcaption></figure>

3. Once copied, paste the channel ID into the Channel ID field in Loadmill.

<figure><img src="../.gitbook/assets/Screen Recording 2024-09-23 at 11.44.28.gif" alt="" width="563"><figcaption></figcaption></figure>

More about our privacy policy can be found [here](https://app.loadmill.com/assets/privacy-policy.pdf)

