# OpenAPI upload

Uploading OpenAPI specification file will allow the mapping of all the APIs at once and creates full visibility on the coverage of tests executions.

To upload a swagger file, follow the next steps:

1. From the dotted menu at the top-right corner of the screen, select "Import from OpenAPI"\
   ![](<../../../.gitbook/assets/image (19).png>)
2. Select the file and proceed with the upload

{% hint style="info" %}
Note. Loadmill will use `servers` section to map the name/domain of the service. In case the `servers` section is missing, a prompt will be displayed to let the user select how the data should be mapped.
{% endhint %}

3. In case Loadmill couldn't find the information, the user will be prompted to select the service.

<figure><img src="../../../.gitbook/assets/image (26).png" alt=""><figcaption><p>Service selection screen, will pop up if servers information is absent in the openAPI specification</p></figcaption></figure>

{% hint style="info" %}
The service name field will allow both, selection and free text.\
If you want to introduce a new service write it down and select it from the dropdown when finished.\
<img src="../../../.gitbook/assets/image (29).png" alt="" data-size="original">
{% endhint %}

4. Click on Import\
   The result will be reflected as new/merged api endpoints, either to new or existing service.

Notes:

* Loadmill currently support OpenAPI specification v3.0, It is possible to convert older and Swagger formats to OpenAPI specification via [this swagger editor.](https://editor.swagger.io/)
