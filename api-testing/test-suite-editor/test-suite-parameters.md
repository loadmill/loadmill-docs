# Test Suite Parameters

The Test Suite Parameters tab allows to configure default parameters which are relevant to the execution context. e.g. target host, login credentials, and user input.

Default parameters can be used in requests using the template strings notation: `${parameter_name}`.

![](<../../.gitbook/assets/Screenshot (22).png>)

![](<../../.gitbook/assets/Screenshot (23).png>)

### Parameters scope

By default, Test Suite parameters have the **Entire Test Suite Run **execution scope. The alternative option is to select the **Single Flow Run **scope.

![](<../../.gitbook/assets/Screenshot (24).png>)

Look at the example below to better understand what execution scopes mean.

Let's say, I have a test flow where I test creating and editing a blog post. I've extracted ID of the post that has been created and now I want to use it in the following requests of the same flow. This is a classic example of a self-contained test and It will work regardless of the execution scope selected. But in case I would like to use the post ID parameter in another flow of the Test Suite I should use the "Entire Test Suite Run" scope, otherwise, Loadmill won't recognize that parameter.

### Support

We are always here if you need any help! Click on the bubble chat button in the lower-right corner of the screen or drop us a line at [support@loadmill.com](mailto:support@loadmill.com).
