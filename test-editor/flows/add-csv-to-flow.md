# Add CSV to Flow

When you're ready to take your automation testing to the next level, it's time to start thinking about testing your flow with multiple variations. This means creating different versions of your test cases and running them against different versions of your software. Doing this can help you find bugs that only show up in specific combinations of your software.

This is important because it helps to ensure that your tests are comprehensive and that they cover all possible scenarios. Creating multiple variations of your tests also allows you to test different parts of the API in isolation, which can be helpful in identifying issues.

Loadmill provides a quick, easy method in testing different iterations of your flow by simply uploading a CSV file containing the different iteration values.

Here's an example for a user management application. This app allows you to add and remove users from your dashboard.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FY6ZSkslC4Klog5DLgXzS%2Fuser-management-app.mp4?alt=media&token=7f4ac56d-00a5-408d-a734-f16bc5c1b090" %}

To start with, let's try 5 different email addresses, as well as 5 first names and 5 last names. We'll divide the task into 4 easy steps.&#x20;

### Create a CSV file.

The following table shows the variations we want to test.

{% hint style="info" %}
The <mark style="background-color:yellow;">**expected\_outcome**</mark> will not be uploaded to the test. This is simply to show you the expected outcome for each variation tested.
{% endhint %}

<table><thead><tr><th width="244">email</th><th>first_name</th><th>last_name</th><th>expected_outcome</th></tr></thead><tbody><tr><td>variation1@loadmill.com</td><td>John</td><td>Doe</td><td>pass</td></tr><tr><td>variation2@random.com</td><td></td><td>Doe2</td><td>pass</td></tr><tr><td>variation3</td><td>VariationThree</td><td></td><td>fail > wrong email</td></tr><tr><td>variation4@</td><td>John4</td><td>Doe_4</td><td>fail > wrong email</td></tr><tr><td>variation45@company</td><td>John_</td><td>$</td><td>fail > wrong email</td></tr></tbody></table>

### Update parameter names.

The _<mark style="background-color:blue;">"Create a user"</mark>_ API contains hard-coded values that need to be substituted with the parameter names from the CSV headers (_**email**, **first\_name** and **last\_name**_).

To do that, replace the string value to ${...parameter name...}. The ${} wraps the values you set on your CSV file by pointing the parameter name to the column header name.

Request Body (before)

```json
{
  "email": "${__escape_quotes(email_in_request_body_1)}",
  "firstName": "John",
  "lastName": "Doe",
  "customId": "johndoe@loadmill.com",
  "environmentId": "da7167ae9563468a9bcb6eb157011745",
  "tenants": [
    "e7f403f4c30d4bc3840456a7953bedb4"
  ]
}
```

Request Body (After)

```json
{
  "email": "${email}",
  "firstName": "${first_name}",
  "lastName": "${last_name}",
  "customId": "johndoe@loadmill.com",
  "environmentId": "da7167ae9563468a9bcb6eb157011745",
  "tenants": [
    "e7f403f4c30d4bc3840456a7953bedb4"
  ]
}
```

### Upload CSV file.

Now that you're done, the last step is to upload your CSV file by clicking on the CSV button.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2Fj88yPjPQ4JSlKlZpHRRI%2Fupload_csv_to_flow.mp4?alt=media&token=6f2ed4d4-eccd-4ac4-bd0b-22e2cf0e508e" %}

### Run the suite.

By running the suite, we see the 5 iterations of the flow we created, each sending the server the values from the uploaded CSV.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FHb2ec5FflCj3nxwEV2D8%2Fiteration_process.mp4?alt=media&token=ead28d3a-92cb-4567-9610-71e2a97f1064" %}

We notice that the last two test iterations have passed when the expected outcome would have been to fail. That is a crucial part in testing your server as it allows you to understand how your API behaves in those scenarios.

Overall, creating multiple variations of your API tests is important because it helps to ensure that the API is functioning correctly and that it meets all expectations. By doing so, you can avoid potential issues and ensure that your API is ready for production.
