# API Testing FAQs

**Functions**

Q: I extracted a few parameters and I want to assign them values with random numbers or characters. Is there a way to do that?

A: Sure, you can use the ‘ \_\_random\_chars\(\[length=10\]\)’ or ‘\_\_random\_number\(\[max\],\[min=0,max=2^32\]\)’, find more useful parameters [here](https://docs.loadmill.com/api-testing/test-suite-editor/functions#randomization-functions).

Q: I’m getting id of my resource and I want to make sure it is in the format of UUID. How can I do that?

A: You can easily do that by creating a new parameter that contains the extracted id and assigning to it value - [${\_\_is\_uuid\(extracted\_id\)}](https://docs.loadmill.com/api-testing/test-suite-editor/functions#__is_uuid-target). Then you can create an assertion that checks the parameter exists. See an example below:

![extracted parameter](../.gitbook/assets/extracted_id.png)

![assertion for the extracted parameter](../.gitbook/assets/assertion_extracted_id.png)

  


  


