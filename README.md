# FAQ

## What is Loadmill and what can it do for me?

Loadmill is an online platform in which you can create and execute load tests for your application. It differs from other services due to its usage of real web traffic to generate the load on the tested server. This allows us to test your application from countless geographic locations and computers - simulating real usage patterns more authentically.

Since we use existing user sessions rather than virtual machines, we are able to offer this service with a much simpler and more affordable pay-as-you-go pricing model.

If you'd like to learn more, have a look at [This video](https://youtu.be/d9DpWolfapE) - it explains the general idea.

## What can’t it do?

Loadmill does not simulate browser/client side activity in any way - we test your server from the network layer and provide advanced parameterization capabilities to let you define the flow of information from one request to the next.

## What is a load/performance test?

According to [Wikipedia](https://en.wikipedia.org/wiki/Load_testing):

> Load testing is the process of putting demand on a application and measuring its response. Load testing is performed to determine a system's behavior under both normal and anticipated peak load conditions.

## I don’t have an application or website to test, what can I do?

You can use the app from this [GitHub repository](https://github.com/idoco/ghost-test-app#deploying-on-heroku).

The simplest way to get going is to create a [Heroku](https://www.heroku.com) account and then click the “Deploy to Heroku” button in the link above. Ido made a [demo video](https://youtu.be/qZd38HhQqiU) in which he is running a test on this app.

## But I don’t want an app, cause… I’m not a programmer!

There are two sides to our platform, the one we haven’t mentioned yet is our [Affiliate Program](https://www.loadmill.com/join-affiliate). If you own or represent any kind of web site then it might interest you. [This video](https://www.youtube.com/watch?v=6Effnw38oog) is less technical and demonstrates how becoming a Loadmill Affiliate can help make you money!

## How can I get more credit to run tests?

If you’re one of our closed beta users \(or want to be\) we can perhaps get you some more credit. Please contact [admin@loadmill.com](mailto:admin@loadmill.com).

## I'm getting an error like “Request has been terminated ... Origin is not allowed by Access-Control-Allow-Origin”, WTF?

Well, odds are you haven’t enabled CORS for our domain in your app’s server. Please follow [these instructions](testing-with-cors.html).

## How to report bugs?

You can send bug reports to [support@loadmill.com](mailto:support@loadmill.com)

