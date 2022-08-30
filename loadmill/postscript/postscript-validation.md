---
description: Running and validating code from postscript
---

# Postscript Validation

Postscript lets you write and run javascript code on every API response of your flow, allowing you to extract or assert parts of the response in a considerable way to validate your flow accurately.

**Say you have an API call that returns an array of fruits and their properties and you want to verify that a specific fruit is inside that list.**

****

To better understand this validation, consider the following javascript variable:

```javascript
const fruits = [
    {
     name:"Banana",
     id: 1
    },{
     name:"Orange",
     id: 2
    },{
     name:"Apple",
     id: 3
    },{
     name:"Mango",
     id: 4
    }
   ]
```

There are many ways to verify if `"Orange"` is part of the list. In this example, we’ll use the `Array.some()` method on the array.

{% code overflow="wrap" %}
```javascript
const orangeOnList = fruits.some((fruit)=>fruit.name == "Orange") // returns true
```
{% endcode %}

Similarly, when an API returns an array of fruits and their properties, you can validate the existence of a specific fruit with the exact same code.

{% hint style="info" %}
**Note: The $ (dollar sign) returns the entire API response in object type.**
{% endhint %}

```javascript
const fruits = $; // returns the entire json response in object type.
const orangeOnList = fruits.some((fruit)=>fruit.name == "Orange") // returns true
```
