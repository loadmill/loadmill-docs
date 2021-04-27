# Extractions - Set Parameters

Use the **Extractions - Set Parameters** section of the request to extract values from the responses. These extracted values can be use in any of the following requests or to assert and verify your success criteria. 

![](../../.gitbook/assets/screen-shot-2021-03-10-at-11.48.41.png)

## Extraction Types

### Assign

Use this to assign any combination of existing parameter or response values to another parameter

![](../../.gitbook/assets/screen-shot-2021-03-10-at-11.51.03.png)

### JSONPath

Use this extractor to extract values from JSON responses. JSONPath is a query language for JSON objects, much like XPath for XMLs.

![](../../.gitbook/assets/screen-shot-2021-03-10-at-11.53.21.png)

You can easily find a relevant JSON Path expression by using our JSON Path Finder feature. To use it, just run your test flow, go to the Response body section, click on JSONPATH and copy the JSON Path expression you need.

![](../../.gitbook/assets/screenshot-2021-04-27t100829.297.png)

![Copying a JSON Path expression from the finder](../../.gitbook/assets/screenshot-2021-04-27t101046.687.png)

Also find helpful JSON Path expressions [here](https://goessner.net/articles/JsonPath/index.html#e2). 

### Clojure

Use this extractor to extract values from Clojure \(EDN content type\) responses. You need to enter JSONPath Query, Clojure queried as JSON.

![](../../.gitbook/assets/screen-shot-2021-03-10-at-16.05.16.png)

### jQuery

Use this extractor to extract values from HTML or XML responses. jQuery extraction syntax is very similar to XPath and may be very useful to extract values from HTML pages \(such as [security tokens](https://portswigger.net/web-security/csrf/tokens)\).

![](../../.gitbook/assets/screenshot-2021-03-10t115521.589.png)

### RegExp

Use this extractor to extract values from any type of response using RegExp. The first value captured by the regex \(in parentheses\) will be set as  the parameter's value. You can test your regex expressions using this useful online tool - [link](https://regex101.com/).

![](../../.gitbook/assets/screen-shot-2021-03-10-at-11.59.32.png)

### Header

Use this extractor to extract values from any of the response headers. 

![](../../.gitbook/assets/screen-shot-2021-03-10-at-16.10.35.png)

## Suggestions

In many cases Loadmill users are using the same extractions and [assertions](https://docs.loadmill.com/api-testing/test-suite-editor/assertions). We've implemented the Suggestions feature that allows team admins to configure a repository of extractions and assertions within Settings - Suggestions. Then, all users can add the extractions from the repository by clicking on **+ SUGGESTIONS**.

![](../../.gitbook/assets/screenshot-2021-03-10t161839.713.png)

By default, there are a few common extraction and assertion examples in the repository. Team admins can also navigate to the Suggestions Settings directly from within the suggestion dialog window.

![](../../.gitbook/assets/screenshot-2021-03-10t163055.050.png)

## Autocomplete

{% hint style="info" %}
🧙♂ Use the autocomplete option to see a list of existing parameters. To see it, press Shift + Cmd \(Ctrl for Windows\) + Space. See how it works below.
{% endhint %}

![The Autocomplete feature](../../.gitbook/assets/ezgif.com-gif-maker-5-.gif)

