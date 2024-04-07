# Datadog Integration

<figure><img src="../.gitbook/assets/image (160).png" alt=""><figcaption></figcaption></figure>

Datadog is a rich analysis observability tool for development stake-holders. Among it's capabilities are performing BI analysis, custom slicing and graphing on logs and tests data, monitoring and more.

Loadmill integrates easily with Datadog and unlocks visibility on loadmill's tests executions inside Datadog and a uniform approach for application and tests execution data analysis.

<figure><img src="../.gitbook/assets/ImageBeginning.jpg" alt=""><figcaption><p>Graphs that can be prepared in Datadog based on loadmill's data</p></figcaption></figure>



### Integration

In loadmill, head to the 'integrations' section under configuration and select 'Datadog'

<figure><img src="../.gitbook/assets/image (172).png" alt=""><figcaption><p>Connect Loadmill to Datadog</p></figcaption></figure>

Insert your datadog's site domain (ie. app.datadoghq.eu) and an api key that is available under API-Keys in Datadog's organizational settings.&#x20;

\
Within Datadog, users are able to view execution-data based on tests execution events. \
Loadmill will push execution data on every tests plan run.

<figure><img src="../.gitbook/assets/image (162).png" alt=""><figcaption><p>Loadmill test results in Datadog</p></figcaption></figure>
