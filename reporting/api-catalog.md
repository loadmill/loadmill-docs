# API Catalog

Loadmill seamlessly identifies and tracks tested system APIs throughout the test creation and execution phases. Our platform maintains an API Catalog, serving as a centralized repository for all tracked APIs. Users have the option to upload a Swagger file to enrich API tracking, providing a complete picture of the system's API landscape.

### Unique Entity ID's Mapping

Define unique entity ID formats to prevent duplicate APIs and streamline catalog organization.

For example:

A request to the same route is made multiple times within a Test Plan:

<figure><img src="../.gitbook/assets/image (12).png" alt=""><figcaption></figcaption></figure>

In all requests, the route is the same. First, `post_by_uuid`, and then a random uuid. Loadmill, after analyzing all service's API calls within the tests, will detect the changing uuid, and display the assumed format:

<figure><img src="../.gitbook/assets/image (15).png" alt=""><figcaption></figcaption></figure>
