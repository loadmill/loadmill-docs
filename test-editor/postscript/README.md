---
description: Create and run various assertions by adding custom codes.
---

# Postscript

Developers are always looking for ways to make their lives easier and writing code is no different. In this section, we'll take a look at how post-request scripts (or postscripts) can help you streamline your HTTP requests. Postscripts are small pieces of code that you can use to automate parts of the request-response cycle.

### Writing Postscripts

With Loadmill, writing Postscript code is as easy as writing plain javascript. The server response is stored into an identifier shown as a dollar sign (`$`). To access specific parameter values we would use the same method as we would when accessing an object:

```javascript
const apple = {
        "genus": "Malus",
        "name": "Apple",
        "id": 6,
        "family": "Rosaceae",
        "order": "Rosales",
        ...
    }
const appleFamily = apple.family; // returns "Rosaceae"
```

Similarly, when receiving a server response, we would view it the same:

```javascript
const response = $; //returns the complete server response
const responseProperty = response.propertyName; // or response["propertyNameavascript"]
// returns the accessed property value inside the response
```

### Accessing Postscript Extractions

The Postscript feature is very useful when you want to use coded variables on different API requests. With this feature, you can access then throughout your automated flow. This is helpful when you need to store and use information from a previous API request in subsequent requests.

In this test case we have an API returning a list of fruits as a `JSON` object. \
From that list, we'll be extracting the name and the calories from the "Apple" object and use it on our next requests:

```javascript
const apple = $.find((fruit)=>fruit.name == "Apple");
// the $ represend the whole json object
// we then use an array method to find the "Apple" object
```

We can now access this object and it's attributes such that:

```javascript
const appleName = apple.name; // returns "Apple"
const appleCalories = apple.nutritions.calories; //returns 52
```

To test this out we can use the console.log method to print out appleName and appleCategories

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FWzhScGnpIURDCl2QxolS%2Fpostscript-intro-1.mp4?alt=media&token=2aafc9d6-c4fd-4ae9-b7cc-daaa060280c7" %}

You can now access those variables within the rest of your flow.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2F2r4lY2krQmYjLZjcJwyM%2Fpostscript-intro-2.mp4?alt=media&token=0309b4cf-754d-4a9d-b5f7-adb26c4f0690" %}

### Freedom of Coding

Postscript is a powerful tool that gives you complete control over the API. With just a few lines of code, you can create conditions, loops and functions for your API tests. Developers find it useful because they can test their APIs the same way they would in a standard programming language.

In our previous example, we tested Fruits API to better understand the Postscript execution. We will now explore the freedom of building code from our API. Here, we'll create a new array containing all the fruits family.

```javascript
const fruits = $; //returns all fruits in JSON
const fruitsFamily = [];
for(var i = 0; i<fruits.length; i++){
  if(!fruitsFamily.includes(fruits[i].family)){
     fruitsFamily.push(fruits[i].family)
  }
}
```

We now created a new array stored in a variable called `fruitsFamily` that can be accessible throughout the automated test case.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FEEcUS7xS2GNaIcyRlnUj%2Fpostscript-intro-3.mp4?alt=media&token=5184346f-8893-4383-ae4d-cc8f41fbc51c" %}

### Debugging Postscript

Debugging your API with Postscript is a crucial part of building an efficient test case and solid product. Some API requests may return values that are not of the same type or may have wrong or unexpected values for various reasons.&#x20;

Postscript allows you to apply logging methods inside your API request the same way you would log any message or value on the web console. It provides an easy debugging and understanding of all the logged values you're extracting or building.&#x20;

Using the same example above, a new array is created by looping over the entire JSON response and extracting the fruits family and adding it to the array. To validate it we use `console.log` to output the result.

```javascript
const fruits = $; //returns all fruits in JSON
const fruitsFamily = [];
for(var i = 0; i<fruits.length; i++){
  if(!fruitsFamily.includes(fruits[i].family)){
     fruitsFamily.push(fruits[i].family)
  }
}
console.log(fruitsFamily) //
```

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FXWFRRTwLmRmFro0YEhFT%2Fpostscript-log.mp4?alt=media&token=e7787aea-5e72-465f-b16e-892f56fd1915" %}
