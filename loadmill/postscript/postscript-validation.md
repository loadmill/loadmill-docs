---
description: Running and validating code from postscript
---

# Postscript Validation

Postscript lets you write and run javascript code on every API response of your flow, allowing you to extract or assert parts of the response in a considerable way to validate your flow accurately.

**Say you have an API call that returns an array of fruits and their properties and you want to verify that a specific fruit is inside that list.**

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FEKWCbzNpqzNkAB7uaeYF%2Fpostscript_1.mp4?alt=media&token=0e318ae5-770c-4f23-b8c2-9dad349c7875" %}

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

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FbH4MezCbfGzYBg8rRr9m%2Fpostscript_1.mp4?alt=media&token=ba184084-354e-4555-80a2-c111a230e414" %}

```javascript
const fruits = $; // returns the entire json response in object type.
const orangeOnList = fruits.some((fruit)=>fruit.name == "Orange") // returns true
```

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FJuyy1pQRtnyJfVVu78w5%2Fpostscript_3.mp4?alt=media&token=fce72b47-6a3f-4c01-98d3-88d17477b3ef" %}
