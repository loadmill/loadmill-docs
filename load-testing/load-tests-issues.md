---
description: Debugging some common issues with load tests
---

# Load Tests Issues

#### Load test does not start

If your test is stuck at "Pending" state, it is possible that some of its  requirements are not being met. For example, if your test is using crowdsourced traffic from a specific country, but there not enough simulation devices are available from this location, your tests will wait in "Pending" state until those will becomes available. 

#### Error message: domain name \[domain\] is not on white list

As mentioned in the [domain verification ](setup/domain-verification.md)page, you are only allowed to test websites that you own. Before your test starts, the list of participating domains \(white list\) is calculated based on all of the test requests. In case one of you request uses a dynamic parameter to generate one of the test request's URL, we might miss this domain, and not add it to the test's white list.

![HTTP request domain name \[random-website-name.com\] is not on white list](../.gitbook/assets/image%20%2817%29.png)

A simple workaround would be to add at least one request for the dynamic domain in one of the other requests. \(If you want you can even use a skip condition disable this request from actually running\)

