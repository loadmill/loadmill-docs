---
description: Validating postscript values
---

# Asserting Postscript

Most scenarios with postscript require you to validate specific values to ensure a successful API test flow. Loadmill provides 2 methods in validating postscript values: Using Mocha or Assertions.

#### Postscript & Mocha

Mocha is a JavaScript test framework making asynchronous testing very simple. Mocha tests run serially, allowing for flexible and accurate reporting, while mapping uncaught exceptions to the correct test cases.

In the previous article we showed how to verify if a value exists in an array or API response. In our example we tested with a fruits API that returns a list of fruits with their properties and verified if a specific fruit was part of that list.&#x20;

```javascript
const fruits = $; // returns the entire json response in object type.
const orangeOnList = fruits.some((fruit)=>fruit.name == "Orange") // returns true
```

In order to validate the API based on the value of orangeOnList we would add the following line of code:

```javascript
//assert.equal(parameter, value)
assert.equal(orangeOnList, true)
```

You can reference yourself with the Mocha documentation for more useful functions to better test your API flows at [https://mochajs.org/](https://mochajs.org/)



#### Postscript & Assertion

Another way to validate a value from postscript is via the Assertion section of the API container. Once your value is saved in a variable, you can use that variable for validation.

{% hint style="warning" %}
Make sure to convert any variable to a string type while using the Assertion section.
{% endhint %}

In this case our code should look like the following:

```javascript
const fruits = $; // returns the entire json response in object type.
const orangeOnList = fruits.some((fruit)=>fruit.name == "Orange").toString() // returns "true"
```

This now converts the boolean value `true` to a string type.

To validate your API based on orangeOnList:

1. Add an Assertion.
2. Select/type isOrangeOnList on the parameters list.
3. Select “Equals” from the Values dropdown.
4. Type `true` on the field.
5. Run your API test.
