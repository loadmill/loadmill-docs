---
description: Streamline Your CI Testing With Loadmill's Datadog Integration
---

# Datadog Integration

Datadog is a rich analysis and observability platform for engineering stakeholders. Its capabilities include performing BI analysis, custom slicing and graphing on logs and test data, monitoring, and more. Loadmill users can report their test executions to [Datadog's CI visibility product](https://www.datadoghq.com/dg/software-delivery/ci-test-visibility/) and offer a single pane of glass for all of their test results within Dadadog.

<figure><img src="../.gitbook/assets/image (161) (1).png" alt=""><figcaption><p>Loadmill test results in Datadog</p></figcaption></figure>

Once the data is reported and collected in Datadog, users can integrate it into their existing dashboards and create a new layer of visibility into the health and performance of their automated tests.

<figure><img src="../.gitbook/assets/image (160).png" alt=""><figcaption></figcaption></figure>

<figure><img src="../.gitbook/assets/ImageBeginning.jpg" alt=""><figcaption><p>Graphs that can be prepared in Datadog based on loadmill's data</p></figcaption></figure>

### Integration Instructions

In loadmill, head to the 'integrations' section under configuration and select 'Datadog'.

<figure><img src="../.gitbook/assets/image (172).png" alt=""><figcaption><p>Connect Loadmill to Datadog</p></figcaption></figure>

Insert your Datadog's site domain (e.g., app.datadoghq.eu) and an API key that is available under API Keys in Datadog's organizational settings. \\

Within Datadog, users are able to view execution data based on test execution events.\
Loadmill will push execution data on every test plan run.
