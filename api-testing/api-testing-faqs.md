# API Testing FAQs

### **Functions**

**I extracted a few parameters and I want to assign them values with random numbers or characters. Is there a way to do that?**

Sure, you can use the ' \_\_random\_chars\(\[length=10\]\)’ or ‘\_\_random\_number\(\[max\],\[min=0,max=2^32\]\)’ functions, find more information on [this page](https://docs.loadmill.com/api-testing/test-suite-editor/functions#randomization-functions).

**I’m getting id of my resource and I want to make sure it is in the format of UUID. How can I do that?**

You can easily do that by creating a new parameter that contains the extracted id and assigning to it value - [${\_\_is\_uuid\(extracted\_id\)}](https://docs.loadmill.com/api-testing/test-suite-editor/functions#__is_uuid-target). Then you can create an assertion that checks that the parameter exists. See an example below:

![extracted parameter](../.gitbook/assets/extracted_id.png)

![assertion for the extracted parameter](../.gitbook/assets/assertion_extracted_id.png)

### **Import**

**Can I import a Postman collection to Loadmill?**

Yep. First, export the collection from Postman by clicking on three dots within the collection and choosing Collection v2.1 \(recommended\). 

![](../.gitbook/assets/ezgif.com-gif-maker-15-.gif)

Then, go to Loadmill and import the collection as a Test Suite.

**Is there a way to import HAR files?**

Sure. Go to the relevant Test Suite - press "IMPORT FLOW" - select your HAR file - choose domains and a new flow will be created.  


  


  


