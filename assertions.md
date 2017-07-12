# Assertions

When testing an API, it is usually not enough to verify that all our HTTP requests completed successfully. Often, it is necessary to make sure that we got the correct response from the server by examining the **response status, body or headers**.

With [Loadmill](https://www.loadmill.com), this is made easy by using **Assertions**. Assertions are used in conjunction with [parameters](parameters.html#parameter-extraction) to do just that: examine the server's response and assert its correctness.

You may have an arbitrary number of assertions executed after each successful request. If an assertion fails, the next request will **not be executed** and the test scenario will be marked as **failed**, but the subsequent assertions for the current request **will be executed** nontheless.

## Assertion Types

The target of an assertion is always a parameter value. You may use built-in parameters, default parameters or any parameter extracted from the current or previous requests in the **current scenario** as the target.

There are several types of assertions:

1. **Not Empty** - the target is a non-empty string.

2. **Equals** - the target is equal to the given expression. The equality check is **case sensitive**.

3. **Contains** - the target contains the given expression. The containment check is **case sensitive**.

4. **Matches JS RegExp** - the target matches the given regular expression.

You may embed parameters in any assertion expression. These parameters will be evaluated right before the assertion is executed.

## Caveats

Keep in mind that all parameter values are **textual**, i.e. a parameter has **no type** such as `Number` or `Array` that we know from common programming languages.

This is important in order to avoid confusion when using parameter extractors such as **JSONPath**. For example, consider the following scenario:

1. Extract the value for `books` via the JSONPath query `student.books` on 
```json
    {
        "student": {
            "books": []
        }
    }
```
2. Assert `books` is **Not Empty**.

You may expect this assertion to fail but, in fact, it will succeedd. This is because the parameter `books` is evaluated to `[]` and therefore constitues a non-empty string. One possible way to correct this is to use a **RegExp** assertion instead: `\[[^\s]+\]`.