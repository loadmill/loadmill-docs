# gRPC Support

Loadmill supports gRPC-based testing. You can easily create gRPC test flows and validate your services in the same streamlined process as with other protocols.

### **Usage**

To execute a gRPC request:

* Go to the relevant test flow within your Test Suite.
* Set the Request URL using `grpc://<dns>` (replace `<dns>` with your target service’s DNS). Typing `grpc://` will automatically adjust the request settings for gRPC usage.
* Once the gRPC protocol is detected, Loadmill will automatically extract and offer gRPC method options based on the uploaded `.proto` files.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FDngNRNnfr14qT19ztrzQ%2FScreen%20Recording%202024-10-15%20at%2014.26.21.mp4?alt=media&token=772ffc5f-8bf3-4d4d-ab83-d92917af6b1e" %}

### Uploading service definitions (.proto files)

Loadmill automatically offers the available gRPC methods after recognizing the gRPC protocol and parsing your `.proto` files.&#x20;

Go to Service Definitions section:

<figure><img src="../.gitbook/assets/image (189).png" alt=""><figcaption></figcaption></figure>

Inside, create a new Service Definition, and upload your `.proto` file/s.

<figure><img src="../.gitbook/assets/image (190).png" alt=""><figcaption></figcaption></figure>

The service definitions will be parsed, and method names will be extracted.&#x20;

To configure service definitions for use in your flow:

* Click on the three dots on the top right
* Choose "Configure Service Definition"
* Pair your Service Definition to your Test Flow

Once the service is paired, the methods will be automatically offered within the flow editor.&#x20;

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FES1uTIFgTXfdFCSvOcaV%2FScreen%20Recording%202024-10-15%20at%2016.54.40.mp4?alt=media&token=d0c4370e-bc21-453e-af6e-2d81638dc91a" %}

