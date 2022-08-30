---
description: Create and run various assertions by adding custom codes.
---

# 🧑‍💻 Postscript - run code

Loadmill provides a wide range of features that you may use in your tests. Having said that, sometimes you may find yourself needing to create a custom validation or it is just more intuitive for you to write a piece of code instead of using the GUI. So, we’ve got it covered by introducing the **Postscript request section**.

![](<../../../.gitbook/assets/Screen Shot 2022-08-17 at 15.41.44.png>)

{% hint style="info" %}
The Postscript section is disabled by default but we are happy to enable it for you. Just drop us a line at support@loadmill.com or chat with us by clicking <img src="../../../.gitbook/assets/screen-shot-2021-08-29-at-11.46.36.png" alt="" data-size="line"> in the lower-right corner of the screen. ‌
{% endhint %}

The Postscript section within requests allows inserting Javascript (JS) code that may contain parameter extractions, custom assertions (validations), and much more. ‌

## Adding JS Code ‌

Let's take a look at a very simple example showing how Postscript works. ‌

![](<../../../.gitbook/assets/Screen Shot 2022-08-17 at 15.51.20.png>)

```
// Creating a new parameter named myFruit and assigning the "fruit" property from the response.
const myFruit = $.fruit;

 // Asserting that the "myFruit" value equals 'banana'.
assert.equal(myFruit,'banana');
```

In the example above, we have the response body that is an object {“fruit”:”banana”}. By using Postscript, we can access the response body value ‘banana’ and then assert it:

`const myFruit = $.fruit;` - here we access the response body value by using JSONPath expression - $.fruit and assigning “my\_fruit” with the fruit property.

`assert.equal(myFruit,'banana');` - then, we add the assertion validating that “myFruit” equals ‘banana’. Postscript uses the assert Node.js module, find more info about it [here](https://nodejs.org/api/assert.html). Let’s say we have a bug and API returned my\_fruit equals ‘apple’ for some reason, so the test will fail and we’ll get an error message like this:

![](<../../../.gitbook/assets/Screen Shot 2022-08-17 at 15.55.54 (1).png>)

## Test Flow example

Below is an example of a similar scenario that we covered above. Go ahead, copy & paste it to your suite and see live how Postscript works! :tada:

```
{ "url": "httpbin.org/anything", "delay": "", "stopBefore": "", "description": "My awesome request", "method": "POST", "expectedStatus": "SUCCESS", "postScript": "const my_fruit = $.json.fruit; // Extracting the response body value and assigning my_fruit with the \"fruit\" property.\n\nassert.equal(my_fruit,'banana'); // Asserting that the \"my_fruit\" value equals 'banana'.", "timeout": 60000, "postData": { "text": "{\"fruit\":\"banana\"}", "mimeType": "application/json" }, "headers": {}, "extract": [], "assert": [], "parameters": null }
```

![](../../../.gitbook/assets/video1880224113-online-video-cut.gif)

## Important notes when using Postscript ‌

1. Supported scripting languages: Javascript.
2. Supported parameter extraction types: JSONPath. Others are coming soon. Meanwhile, if you are using another Extraction type like jQuery, Clojure etc, you can extract a parameter within [Extractions](https://docs.loadmill.com/api-testing/test-suite-editor/set-parameters-extractions) and use it for validations in Postscript.
3. Note, when using parameters from Extractions, it will give you a string value. If you want to use it as a non-string value in Postscript, you should JSON.parse it first:

![](<../../../.gitbook/assets/Screen Shot 2022-08-17 at 16.13.31.png>)

4\. Loadmill [built-in functions support](https://docs.loadmill.com/api-testing/test-suite-editor/functions): coming soon, stay tuned. 😉

5\. Remember with great power comes great responsibility so use it wisely. 🕷
