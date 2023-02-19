# Loadmill - AI - Powered Solution

Loadmill automates testing across multiple devices and platforms by replaying and analyzing real user behavior, helping engineers to easily create the tests required for continuous delivery. Loadmill creates and replays thousands of tests based on user flows within minutes.

<figure><img src=".gitbook/assets/Mobile testing diagrams_v03b.jpg" alt=""><figcaption></figcaption></figure>

Loadmill's AI-powered test case generator can help you create comprehensive, reliable test cases for your APIs in minutes. By composing API requests and correlating them with Loadmill's algorithms, you can generate dynamic, automated test cases that are ready to use. With Loadmill, you can quickly and easily create comprehensive test suites for your APIs that will ensure their reliability and performance.

Imagine a scenario where you need to add a user to your company’s database by submitting a form and then verifying that a user exists by validating its id provided when it's added to the database.

This is a common process where the form will make a `POST` request to the server. The `POST` request connects to the server location through the server's URL path and passes in the user information inside the body of the request.

If the user has been successfully added, the server sends back the `status 200` of the request notifying the request has been successful and the id of the user that has been added to the database.

![](<.gitbook/assets/image (2) (2).png>)

You'll then make a `GET` request to the server by passing in that response `id` from the previous `POST` request (either inside of the body or in your URL). If everything went right and you're successful, you'll get a response back from your server saying whether or not the user's `id` expired.

![](<.gitbook/assets/image (1) (1) (4).png>)

