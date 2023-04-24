# Quick examples of API requests

If you're looking to make some API requests, here are a few examples to help you get started. Remember, you'll need to set up your server to make these requests - this is just for illustration purposes. To get started, let's look at a simple example.&#x20;

Suppose we want to get information about the latest users on our site. We can do this by making a GET request to the /users endpoint:

In this example, we're using REST API to demonstrate how API calls are being accessed.

{% swagger method="get" path="" baseUrl="/" summary="This will return a JSON object containing information about the latest users." %}
{% swagger-description %}

{% endswagger-description %}

{% swagger-parameter in="body" name="id" type="456" required="true" %}

{% endswagger-parameter %}

{% swagger-response status="200: OK" description="" %}
```javascript
{
    // Response
}
```
{% endswagger-response %}
{% endswagger %}

<mark style="color:red;">**method**</mark>    <mark style="color:blue;">**URL**</mark>\
GET          /users

This will return a JSON object containing information about the latest users.

```
[{
        "name": {
            "title": "mr",
            "first": "ross",
            "last": "geller"
        },
        "id": 123,
        "email": "rossgeller@testmail.com",
        "phone": "011-962-7516",
        "gender": "male",
        "age": "34",
        "occupation": "scientist",
        ...
    },
    {
        "name": {
            "title": "mrs",
            "first": "jennifer",
            "last": "gibson"
        },
        "id": 456,
        "email": "jennifergibson@testmail.com",
        "phone": "212-934-5277",
        "gender": "female",
        "age": "29",
        "occupation": "developer",
        ...
    },
    ...
]
```

Now let's say we want to get information about a specific user. We can do this by making a GET request to the /users/{id} endpoint, where {id} is the id of the user we want to retrieve:

<mark style="color:red;">**method**</mark>    <mark style="color:blue;">**URL**</mark>\
GET          /users/123

```
{
    "name": {
        "title": "mr",
        "first": "ross",
        "last": "geller"
    },
    "id": 123,
    "email": "rossgeller@testmail.com",
    "phone": "011-962-7516",
    "gender": "male",
    "age": "34",
    "occupation": "scientist",
    ...
}
```

This will return a JSON object containing information about the user with id 123.&#x20;

We can also create new users by making a POST request to the /users endpoint. For example, to create a new user with the name "John Doe" and has filled all the required parameters for the server to accept your request, we would make the following request:

<mark style="color:red;">**method**</mark>    <mark style="color:blue;">**URL**</mark>\
POST          /users

```
//Request Body 
{
    "name": {
        "title": "mr",
        "first": "john",
        "last": "doe"
    },
    "email": "johndoe@testmail.com",
}
```

The server would then accept your request and send back a response with a status code 200 (means the request has been successful) and in this case would send back a generated id of the user-created by this request as shown below:

```
//Response Body 
{
    "id":789
}
```
