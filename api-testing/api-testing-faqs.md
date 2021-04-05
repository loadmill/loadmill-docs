# API Testing FAQs

### **I'm testing entity creation where entity Name should be unique. Can I assign a set of random letters to it?**

Sure, create a parameter with using the `__random_letters([length=10])` function for that:

![](../.gitbook/assets/screenshot-2021-04-01t155426.154.png)

Find more great functions on [this page](https://docs.loadmill.com/api-testing/test-suite-editor/functions#randomization-functions) and more information about default parameters [here](https://docs.loadmill.com/api-testing/test-suite-editor/test-suite-parameters). 

### **I'm getting ID of my resource and I want to make sure it is in the format of UUID. How can I do that?**

You can easily achieve that:

1. Extract the ID into a parameter by using JSONPath.
2. Create another parameter by using the extracted ID and [function `__random_uuid()`](https://docs.loadmill.com/api-testing/test-suite-editor/functions#__random_uuid). The output would be "true" if the ID is in the format of UUID. Else, it would be "false".

![](../.gitbook/assets/extracted_id.png)

   3. Now, assert the second parameter you've created earlier.

![assertion for the extracted parameter](../.gitbook/assets/assertion_extracted_id.png)

### \*\*\*\*

  


  


  


