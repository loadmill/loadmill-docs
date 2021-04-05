---
description: Debugging some common issues with load tests
---

# Load Testing troubleshooting

#### Load test does not start

If your test is stuck at "Pending" state, it is possible that some of its requirements are not being met. For example, if your test is using crowdsourced traffic from a specific country, but there not enough simulation devices are available from this location, your tests will wait in "Pending" state until those will become available. 

**I’m getting an error ‘Unverified domains are already under test’ but our domain has been verified. What do I miss here?**

Please make sure your tests are not using other domains like facebook, salesforce etc. Contact support at [support@loadmill.com](mailto:support@loadmill.com) if you need [an additional domain to get verified](https://docs.loadmill.com/load-testing/setup/domain-verification) or any other assistance is required.

**Error message: domain name \[domain\] is not on white list**

As mentioned in the [domain verification ](../getting-started/setup/domain-verification.md)page, you are only allowed to test websites that you own. Before your test starts, the list of participating domains \(white list\) is calculated based on all of the test requests. In case one of your request uses a dynamic parameter to generate one of the test request's URL, we might miss this domain, and not add it to the test's white list.

![HTTP request domain name \[random-website-name.com\] is not on white list](../.gitbook/assets/image%20%2817%29.png)

A simple workaround would be to add at least one request for the dynamic domain in one of the other requests. \(If you want you can even use a skip condition to disable this request from actually running\).

