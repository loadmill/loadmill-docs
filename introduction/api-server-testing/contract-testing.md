# Contract testing

#### Intro

Contract testing is a testing approach used in software development that involves testing the interactions between two different services or systems by defining and verifying the contracts or agreements between them.

In a typical scenario, when two services communicate with each other through an API, the contract testing approach involves defining the expected input and output data for each API endpoint, and then writing tests to verify that the API endpoint behaves as expected.

Contract testing helps in detecting and preventing issues that may arise due to changes made to the API, without having to run end-to-end tests. This allows for faster and more efficient testing of software systems, reducing the time and effort required for testing.

Overall, contract testing helps improve the reliability, stability, and resilience of software systems by ensuring that the different components of the system work together as intended, and are compatible with each other.

#### Contract testing with Loadmill

Contract testing with Loadmill is easy. To create contract validation of an API call, use [JSON schema](../../general/api-testing1/test-suite-editor/assertions.md#json-schema-validate-that-a-parameter-comply-with-given-json-schema.) or [JSON contains](../../general/api-testing1/test-suite-editor/assertions.md#json-contains-validates-that-a-json-contains-a-subset-json-in-such-way-dynamic-fields-can-be-omitted) as following:

*   **Enforcing JSON Schema of an API:** \
    With 'JSON Schema' you can explicitly enforce multiple of aspects of your json data.\
    In the request editor assertions insert new entry, use '\_\_responseBody' built-in parameter and ensure the values are of the type "JSON Schema", then insert a valid json-schema.\


    <figure><img src="../../.gitbook/assets/image (73).png" alt=""><figcaption><p>An example of schema validation request in loadmill</p></figcaption></figure>



In the following table you can see an example of the schema and a typical response that comply with the schema.

<table><thead><tr><th>Schema</th><th>Response</th></tr></thead><tbody><tr><td><pre class="language-json"><code class="lang-json">{
  "$schema": "http://json-schema.org/draft-04/schema#",
  "type": "object",
  "properties": {
    "id": {
      "type": "integer"
    },
    "title": {
      "type": "string"
    },
    "description": {
      "type": "string"
    },
    "price": {
      "type": "integer"
    },
    "discountPercentage": {
      "type": "number"
    },
    "rating": {
      "type": "number"
    },
    "stock": {
      "type": "integer"
    },
    "brand": {
      "type": "string"
    },
    "category": {
      "type": "string"
    },
    "thumbnail": {
      "type": "string"
    },
    "images": {
      "type": "array",
      "items": [
        {
          "type": "string"
        },
        {
          "type": "string"
        },
        {
          "type": "string"
        },
        {
          "type": "string"
        },
        {
          "type": "string"
        }
      ]
    }
  },
  "required": [
    "id",
    "title",
    "description",
    "price",
    "discountPercentage",
    "rating",
    "stock",
    "brand",
    "category",
    "thumbnail",
    "images"
  ]
}
</code></pre></td><td><pre class="language-json"><code class="lang-json">{
   "id":1,
   "title":"iPhone 9",
   "description":"An apple mobile which is nothing like apple",
   "price":549,
   "discountPercentage":12.96,
   "rating":4.69,
   "stock":94,
   "brand":"Apple",
   "category":"smartphones",
   "thumbnail":"https://i.dummyjson.com/data/products/1/thumbnail.jpg",
   "images":[
      "https://i.dummyjson.com/data/products/1/1.jpg",
      "https://i.dummyjson.com/data/products/1/2.jpg",
      "https://i.dummyjson.com/data/products/1/3.jpg",
      "https://i.dummyjson.com/data/products/1/4.jpg",
      "https://i.dummyjson.com/data/products/1/thumbnail.jpg"
   ]
}
</code></pre></td></tr></tbody></table>

*   **Enforcing JSON structure using JSON-Contains:**\
    **'**&#x4A;son-contains' is a lightweight capability in Loadmill to enforce JSON data. \
    In the request editor assertions insert new entry, use '\_\_responseBody' built-in parameter and ensure the values are of the type "JSON Contains", then insert an expected json or a subset that can contain less fields.\
    Note, to ensure existence of a field ignoring it's value use `"*"` notation.

    <figure><img src="../../.gitbook/assets/image (116).png" alt=""><figcaption><p>Json-Contains example in loadmill - Enforcing json content</p></figcaption></figure>

In the following table you can see an example of the expected JSON-Contains object and a typical response that comply with it.

<table><thead><tr><th>JSON-Contains object</th><th>Response</th></tr></thead><tbody><tr><td><pre class="language-json"><code class="lang-json">{
    "id": 1,
    "title": "iPhone 9",
    "description": "An apple mobile which is nothing like apple",
    "price": 549,
    "discountPercentage": "*",
    "stock": 94,
    "brand": "Apple",
    "category": "smartphones",
    "thumbnail": "https://i.dummyjson.com/data/products/1/thumbnail.jpg",
    "images": [
        "https://i.dummyjson.com/data/products/1/1.jpg",
        "https://i.dummyjson.com/data/products/1/2.jpg",
        "https://i.dummyjson.com/data/products/1/3.jpg",
        "https://i.dummyjson.com/data/products/1/4.jpg",
        "https://i.dummyjson.com/data/products/1/thumbnail.jpg"
    ]
}
</code></pre></td><td><pre class="language-json"><code class="lang-json">{
    "id": 1,
    "title": "iPhone 9",
    "description": "An apple mobile which is nothing like apple",
    "price": 549,
    "discountPercentage": 12.96,
    "rating": 4.69,
    "stock": 94,
    "brand": "Apple",
    "category": "smartphones",
    "thumbnail": "https://i.dummyjson.com/data/products/1/thumbnail.jpg",
    "images": [
        "https://i.dummyjson.com/data/products/1/1.jpg",
        "https://i.dummyjson.com/data/products/1/2.jpg",
        "https://i.dummyjson.com/data/products/1/3.jpg",
        "https://i.dummyjson.com/data/products/1/4.jpg",
        "https://i.dummyjson.com/data/products/1/thumbnail.jpg"
    ]
}
</code></pre></td></tr></tbody></table>

```
```

**Automatic assertions**\
Loadmill can generate 'JSON schema' or 'JSON contains' assertions automatically during test composition. Such assertions can serve are a quick baseline that can be adjusted later on.\
To turn automatic JSON validations.

1. head to settings icon -> recordings:\
   <img src="../../.gitbook/assets/image (56) (1).png" alt="" data-size="original">
2.  Locate the 'JSON Validation section in the list', make sure the toggle turned on and adjust the type according to the needs.

    <figure><img src="../../.gitbook/assets/image (59).png" alt=""><figcaption></figcaption></figure>

if 'JSON Validation' section doesn't exist, try adding it by clicking on ![](<../../.gitbook/assets/image (55).png>) at the top right corner and selecting it from the list.

<figure><img src="../../.gitbook/assets/image (64) (1).png" alt=""><figcaption></figcaption></figure>

4. (optional) Click on the '+' to add ignored keys.\
   &#x20;![](<../../.gitbook/assets/image (57).png>)
5. From now on, every generated test with loadmill composers will cary json validation assertions.

