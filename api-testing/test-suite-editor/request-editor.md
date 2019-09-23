# Request editor

Request is the most basic building block of our tests. It represents a single API call or a user action.

![](../../.gitbook/assets/image.png)

#### Advanced request options

When we expand the request editor by clicking the ADVANCED button, we can see that a test request is made of two main sections - The **request section** \(In orange\) and the **response processing section** \(In blue\).  

![](../../.gitbook/assets/image%20%286%29.png)

#### The Request section

![](../../.gitbook/assets/image%20%287%29.png)

* The Method and URL fields are the most basic requirement for a valid request.
* Black input fields are fields in which you can use parameters and functions \(usage of parameters and functions is explained in the next section\)
* It is recommended to set the request description in a way that describes its action. This will make it easier for you to debug your tests later if this request fails.
* Some requests requires a body. Selecting the right content-type for your request body will help us highlight the syntax of your request body \(i.e. JSON or XML\)

#### Response Processing section

![](../../.gitbook/assets/image%20%289%29.png)

The response processing section enables to you extract values from the request's response and validate them.

![](../../.gitbook/assets/image%20%284%29.png)

* You can extract values from the response body into an existing or a new parameter using JSONPath, jQuery, RegExp.
* You can extract an HTTP header value into a parameter using the Header extractor.
* You assign a static value or apply a function on anther parameter using Assign option

Assertions have their own section in the next pages.



