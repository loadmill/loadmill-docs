# Accessing w/ Postscript

The Postscript feature is very useful when you want to use coded variables on different API requests. With this feature, you can access then throughout your automated flow. This is helpful when you need to store and use information from a previous API request in subsequent requests.

In this test case we have an API returning a list of fruits as a `JSON` object. \
From that list, we'll be extracting the name and the calories from the "Apple" object and use it on our next requests.

### Extracting w/ Postscript

```javascript
const apple = $.find((fruit)=>fruit.name == "Apple");
// the $ represend the whole json response object
// we then use an array method to find the "Apple" object
```

We can now access this object and it's attributes such that:

```javascript
const appleName = apple.name; // returns "Apple"
const appleCalories = apple.nutritions.calories; //returns 52
```

To test this out we can use the `console.log` method to print out <mark style="background-color:yellow;">**appleName**</mark> and <mark style="background-color:yellow;">**appleCategories**</mark>

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FWzhScGnpIURDCl2QxolS%2Fpostscript-intro-1.mp4?alt=media&token=2aafc9d6-c4fd-4ae9-b7cc-daaa060280c7" %}

You can now access those variables within the rest of your flow.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2F2r4lY2krQmYjLZjcJwyM%2Fpostscript-intro-2.mp4?alt=media&token=0309b4cf-754d-4a9d-b5f7-adb26c4f0690" %}

### Using Postscript with Pre-Extracted Values

You can use Postscript print out values from the Extractions section used across the flow.

Here are the steps:

1. Create any extraction from the Extractions section.
2. Open your Postscript section.
3. Assign the extracted parameter to postscript. \
   ie: `const name = extractedParameterName;`

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FAInGDNp1CKYv3rB29OXz%2Fextractions-postscript.mp4?alt=media&token=1fcc71a6-74e6-4803-979c-3d0a9af26ce3" %}
