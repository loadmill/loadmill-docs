---
description: Create and run various assertions by adding custom codes.
---

# 🧑‍💻 Postscript - run code

Loadmill provides a wide range of features that you may use in your tests. Having said that, sometimes you may find yourself needing to create a custom validation or it is just more intuitive for you to write a piece of code instead of using the GUI. So, we’ve got it covered by introducing the **Postscript request section**.

![](https://lh5.googleusercontent.com/qcowbEw9nw5WRcTLS5QzqP8GEajDzuq6yUFEEWgmrncusOg7KbjAstMTmxENHVTIgHmuwvXOBfmQ9GcngXgNNYxAU6x2ALwDyBsvz6MmiDytC22Ifa69A-x4DQ1240zsExdHxX2-=s0)

{% hint style="info" %}
The Postscript section is disabled by default but we are happy to enable it for you. Just drop us a line at support@loadmill.com or use ![](../../.gitbook/assets/screen-shot-2021-08-29-at-11.46.36.png) in the lower-right corner of the screen. ‌
{% endhint %}

The Postscript section within requests allows inserting Javascript \(JS\) code that may contain parameter extractions, custom assertions \(validations\), and much more. ‌

## Adding JS Code ‌ 

Let's take a look at a very simple example showing how Postscript works. ‌ 

![](https://lh5.googleusercontent.com/U1nhOMSrsNoZIn7ABYftItHeOqfKsWGL_H5ni54brdvFGt5kdj9D5qK-L4aRirQXOW3hqHxmX1wLmCgbWGCR2qzwamqJPuEPv6NS5w9MtjSZQ3Qo3A8akk8gosooNs06AvXu6ijM=s0)

```text
const my_fruit = $.fruit; // Extracting the response body value and assigning my_fruit with the "fruit" property. 

assert.equal(my_fruit,'banana'); // Asserting that the "my_fruit" value equals 'banana'.// 
```

In the example above, we have the response body that is an object {“fruit”:”banana”}. By using Postscript, we can access the response body value ‘banana’ and then assert it: 

`const my_fruit = $.fruit;` - here we access the response body value by using JSONPath expression - $.fruit and assigning “my\_fruit” with the fruit property.

`assert.equal(my_fruit,'banana');` - then, we add the assertion validating that “my\_fruit” equals ‘banana’. Let’s say we have a bug and API returns my\_fruit equals ‘apple’ for some reason, so the test will fail and we’ll get a pretty error message like this:

![](https://lh4.googleusercontent.com/5YBmZMHNZzksAHzDsp_EVCyC6mYmx36lX5Jv1ILxUpETyAtnUR5DzHqeoB-fGTVS0M0SCbqFTIR9MKmF5eHYV_-q7HFWllRVm2DuWw4gJgKiKq55qrx2BwnbT6nxKPYT7DFJj-sS=s0)

## Test Flow example

Below is an example of a similar scenario we've talked about above. Go ahead, copy & paste it to your suite and see live how Postscript works!  🎉 

```text
{ "url": "httpbin.org/anything", "delay": "", "stopBefore": "", "description": "My awesome request", "method": "POST", "expectedStatus": "SUCCESS", "postScript": "const my_fruit = $.json.fruit; // Extracting the response body value and assigning my_fruit with the \"fruit\" property.\n\nassert.equal(my_fruit,'banana'); // Asserting that the \"my_fruit\" value equals 'banana'.", "timeout": 60000, "postData": { "text": "{\"fruit\":\"banana\"}", "mimeType": "application/json" }, "headers": {}, "extract": [], "assert": [], "parameters": null }
```

![Pasting &amp; running test flow example](../../.gitbook/assets/zoom-0-online-video-cuttercom-on.gif)

## Important notes when using Postscript ‌ 

1. Supported scripting languages: Javascript. 
2. Supported parameter extraction types: JSONPath. Others are coming soon. Meanwhile, if you are using another Extraction type like jQuery, Clojure etc, you can extract a parameter within [Extractions](https://docs.loadmill.com/api-testing/test-suite-editor/set-parameters-extractions) and use it for validations in Postscript. 
3. Note, when using parameters from Extractions, it will give you a string value. If you want to use it as a non-string value in Postscript, you should JSON.parse it first:

![](https://lh6.googleusercontent.com/DlWImjRmBlRIoi6M3TyX_moUe4aWi5GPm1M9dEybYrl3_0VA8S_dL2Bv3rVUrq1QyaqXR2m8RsUJVeIZfKUKGyskXIgZjYAFfJtndO6grfDzZufFH17bGxbpKKuGS6NMYRMHng17=s0)

   4. Loadmill [built-in functions support](https://docs.loadmill.com/api-testing/test-suite-editor/functions): coming soon, stay tuned 😉 

   5. Remember with great power comes great responsibility so use it wisely 🕷

