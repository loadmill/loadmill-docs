# API Catalog

### Overview:

Loadmill seamlessly identifies and tracks tested system APIs throughout the test creation and execution phases. Our platform maintains an API Catalog, serving as a centralized repository for all tracked APIs across all tested services. Users can upload OpenAPI specification files to enrich API tracking, providing a complete picture of the system's API landscape.

<figure><img src="../../../.gitbook/assets/image (1) (1) (1) (2).png" alt=""><figcaption></figcaption></figure>

### Features and capabilities:

Within the API Catalog, users can conveniently view and manage APIs categorized and ordered by groups. Each API entry includes details on which tests cover it, along with timestamps indicating when it was last checked. Additionally, Loadmill will indicate if an API remains uncovered by any tests, effectively pinpointing system blind spots.\


<figure><img src="https://lh7-us.googleusercontent.com/4i13hLhoxqMqnu9a007tBe0O8c_SuQnKjubS2AGe9mVA2pgpK8A7_fcPxYJTz6nAg3k6lyVr2OOscAq3gX818wDmiDut3be8rInx5sIN86uhzrii5NOsnpFP0zmoKQzPVThjGKoj1GJhKXZ4TkZrinw" alt=""><figcaption></figcaption></figure>

* **Multiple Services support** - Maintain separate API catalogs for each service. Generate focused reports specific to individual services, enabling deeper insights into testing efforts.
* **Domain Mapping and grouping** - Naturally same service can be reflected via multiple environments, Loadmill support grouping similar APIs across different environments by mapping domains to services to avoid duplicates.
* **Unique Entity IDs recognition** - Loadmill maps dynamic IDs automatically and displays them as placeholders. In addition, users can define unique entity ID formats for better algorithm recognition, to prevent duplicates, and to streamline catalog organization.
*   **Insights** (in Reports menu) - Loadmill's reports include an Insights section, offering valuable metrics on overall testing activity. Users can track the percentage of APIs tested within a specified timeframe and monitor the detection of new APIs by the system on a daily basis.

    <figure><img src="https://lh7-us.googleusercontent.com/YjYWHUIU78cG51ln0-g7dXvTrLrgvVJtKvFKAaUAjQTGufZCuZ1kPfcls42gvjQX8bxbxJXY8Es_uXL0eegHyshlwNln03FRHqr226JpwdG3X_g3koqGMKr8VHfFzSR7UXSeOOj-dQ8Sup_1ejqygC8" alt=""><figcaption><p>API coverage section in Insights report</p></figcaption></figure>



Notes

* Loadmill will map new API-endpoint in the following occasions:
  * During test creation from capture - driven by example
  * When importing a har file of a captured user behavior
  * When importing a collection (Postman)
  * When active flow is executed as part of plan/suite execution
  * When [importing swagger file](#user-content-fn-1)[^1]
  * When creating a new api manually
* Only successful API requests will be used for API coverage mapping.

[^1]: 
