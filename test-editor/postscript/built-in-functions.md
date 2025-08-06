---
description: Using built-in functions in Postscript
---

# Using Built-in Functions in Postscript

You can use [Loadmill's built-in functions](../../general/api-testing1/test-suite-editor/functions.md) in your Postscript code to perform common operations. You can invoke these functions like you would call it in Loadmill's extractions or assertions.

For example, to add two numbers:

```javascript
const result = __add(1, 2);
console.log(result); // 3
```

Obviously, the `__add` example is a bit simplistic and you can use the JavaScript `+` operator directly, but it illustrates how to use built-in functions.
To really leverage the power of built-in functions, you can use them for more complex operations which are not easily achievable with basic JavaScript.

## More Interesting Examples

Some of Loadmill's built-in functions are very useful and powerful and can help you save time and effort in your Postscript code. Here are a few examples:

```javascript
// Generate a random UUID
const id = __random_uuid();
// Hash a string using SHA-256
const hash = __sha256('mySecret', 'hex');
// Get the next suggested element from full_array which is not in sub_array.
const nextMissingElement = __array_missing_element([0,1,3,4], [0,1,2,3,4,5,6,7,8,9,10]) // returns 2
```

And many more complex operations are available. You can find the full list of built-in functions in the [built-in functions documentation](../../general/api-testing1/test-suite-editor/functions.md).

### ⚠️ String Inputs and Outputs in Built-in Functions

When working with Loadmill's built-in functions in Postscript, **remember that all inputs and outputs must be strings**.
This is a common source of confusion, especially when dealing with complex types like arrays or objects.

For example, this will **not** work as expected:

```javascript
// ❌ Bad: passing arrays directly
const nextMissingElement = __array_missing_element([0,1,3,4], [0,1,2,3,4,5,6,7,8,9,10]);
```

That’s because the function expects string representations of the arrays. To fix this, convert them using `JSON.stringify`:

```javascript
// ✅ Good: Correct usage with JSON.stringify
const array1 = JSON.stringify([0, 1, 3, 4]);
const array2 = JSON.stringify([0, 1, 2, 3, 4, 5, 6, 7, 8, 9, 10]);
const nextMissingElement = __array_missing_element(array1, array2);
const result = JSON.parse(nextMissingElement);
console.log(result); // output: 2
```

Another example:

```javascript
const arrAsString = JSON.stringify([109, 136, 156, 188, 19, 190, 2, 34, 55, 90])
const sortedArr = __array_sort_numbers(arrAsString)
console.log(sortedArr); // output: [2, 19, 34, 55, 90, 109, 136, 156, 188, 190]
```

🔁 Tip: Use `JSON.stringify` for inputs and `JSON.parse` for outputs when working with arrays, objects, numbers or booleans. Never assume the return value is a native type, it will always be a string.
