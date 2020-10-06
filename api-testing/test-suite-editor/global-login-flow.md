# Global Login flow and authentication headers

Within the Login section of each test suite, you can define a short flow that will run **before each test flow**. This setup flow is most commonly used to execute requests that will authenticate the test flow itself via cookies or authorization tokens. This flow can also be used to retrieve and extract data necessary for the execution of your test flows. 

Cookies received and parameters extracted by the login flow request will be accessible by the requests of the actual test flow.

Global authentication headers configured below can use values extracted by the login flow requests and will override matching headers in the test flow requests.

![](../../.gitbook/assets/image%20%2836%29.png)

![](../../.gitbook/assets/image%20%2835%29.png)

