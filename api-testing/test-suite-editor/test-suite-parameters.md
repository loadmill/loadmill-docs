# Test Suite Parameters

The Test Suite Parameters tab allows to configure default parameters which are relevant to the execution context. e.g. target host, login credentials, and user input. 

Default parameters can be used in requests using the template strings notation: `${parameter_name}`. 

![](../../.gitbook/assets/screenshot-2021-03-22t141837.201.png)

![The Test Suite parameter in request](../../.gitbook/assets/screenshot-2021-03-22t141949.485.png)

### Parameters scope

By default, Test Suite parameters have the **Single Flow Run** execution scope. The alternative option is to select the **Entire Test Suite Run** scope. 

![](../../.gitbook/assets/screenshot-2021-03-22t142256.813.png)

![](../../.gitbook/assets/screenshot-2021-03-22t142317.772.png)

Look at the example below to better understand what the execution scope means.

Let's say, I have a test flow where I test creating and editing a blog post. I've extracted ID of the post that has been created and now I want to use it in the following requests. This is a classic example of a self-contained test and It will work regardless of the execution scope selected. But in case I would like to use the post ID parameter in another flow of the Test Suite I should choose the "Entire Test Suite Run" scope.

### Support

We are always here if you need any help! Click on the bubble chat button in the lower-right corner of the screen or drop us a line at [support@loadmill.com](mailto:support@loadmill.com).  







