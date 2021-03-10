# Extractions - Set Parameters

Use the **Extractions - Set Parameters** section of the request to extract values from the responses. These extracted values can be use in any of the following requests or to assert and verify your success criteria. 

![](../../.gitbook/assets/screen-shot-2021-03-10-at-11.48.41.png)

## Extraction Types

### Assign

Use this to assign any combination of existing parameter or response values to another parameter

![](../../.gitbook/assets/screen-shot-2021-03-10-at-11.51.03.png)

### JSONPath

Use this extractor to extract values from JSON responses. JSONPath is a query language for JSON objects, much like XPath for XMLs.

You can test your JSONPath expressions using this useful online tool - [link](https://jsonpath.com/) and see some great examples on this page - [link](https://goessner.net/articles/JsonPath/index.html#e2).

![](../../.gitbook/assets/screen-shot-2021-03-10-at-11.53.21.png)

### Clojure

Use this extractor to extract values from EDN responses. Enter JSONPath Query, Clojure queried as JSON.

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

### Suggestions

Team admins can configure a repository of extractions and [assertions](https://docs.loadmill.com/api-testing/test-suite-editor/assertions) within Settings - Suggestions. By default, there are a few common extraction and assertion examples in the repository. All users can add the extractions from the repository by clicking on **+ SUGGESTIONS**.

![](../../.gitbook/assets/screenshot-2021-03-10t161839.713.png)

Team admins can navigate to the Suggestions repository settings directly from within the suggestion dialog window.

![](../../.gitbook/assets/screenshot-2021-03-10t163055.050.png)

### Autocomplete

{% hint style="info" %}
🧙♂ Use the autocomplete option to see a list of existing parameters. To see it, press Shift + Cmd \(Ctrl for Windows\) + Space. See how it works below.
{% endhint %}

![The Autocomplete option](../../.gitbook/assets/ezgif.com-gif-maker-5-.gif)

