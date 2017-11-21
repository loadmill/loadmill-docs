# Loadmill In 5 Minutes
{% youtube %}
https://www.youtube.com/watch?v=qZd38HhQqiU
{% endyoutube %}

In this quick guide to Loadmill we will learn how to:

1. Create and run a very simple load test in just a few seconds.
2. Record a user session with a browser and import it to Loadmill.
3. Transform the recorded session into an advanced test scenario.
4. Run the advanced load test and analyze the results.

We are going to be testing a [Ghost](https://ghost.org/developers/) publishing service hosted on Heroku that you can actually download/fork and play with yourself if you so desire.

Everything described here is demonstrated in the video above so be sure to check it out.

## Free Account
Before you can start running free tests, you will need to create a Loadmill account. We do not ask for any credit card or personal information other your name and email so it only takes about five seconds. You can also login using your Google or GitHub account.

## Hello World
The simplest load test you can create is an HTTP GET request to your web server. All you need to do is:

1. Click the **NEW TEST** link on the top navigation menu. This will get you to our test editor.
2. Copy and paste the website URL into the **URL** text box. In our case, it's going to be `https://loadmill-test-blog.herokuapp.com`.
3. Click the **LOAD TEST** button and confirm the config by clicking **RUN**.

**Note:** At some point you may notice a message stating that your domain is not _verified_ - this only means that you may not run high volume tests before proving ownership of your domain/hostname. You can ignore it for now and learn how to do that later [here](domain-verification.html) \(it's actually pretty easy\).

That's it! You have just created and ran your first load test in under a minute 🎉

## Record A Session
Any modern browser that has **Developer Tools** such as Chrome, Firefox, Edge or Safari, has a **Network Tab** in which you can view and **record HTTP requests** of your session. If your tested application has a web interface, recording a browser session is a pretty fast and straight forward way to create advanced tests for common user scenarios.

The user story we would like to record is the following:

1. A blogger logs in to the Ghost platform using an email and password.
2. The blogger creates a blog post.
3. The blogger publishes the blog post.

So let's dive right in:

### Setup a recording
Let's assume you're using Chrome to record your session. If you have any other browser with develper tools, the flow will be very similar.

Start by opening the network tab:

![](/assets/net-tab.gif)

Now we shall enter the URL for the login page in the address bar: `https://loadmill-test-blog.herokuapp.com/ghost/signin`. We can already see the network tab below starting to fill up with HTTP requests sent by the browser to our web server. We would like the first request to be the login, so just click on the clear button on the top left corner of the network tab to get rid of these.

We are ready to start recording.

### Do stuff
The next step is to simply do what the user in our scenario is supposed to do. In our case it is:

1. Enter the mock user email `a@b.com` and password `Test1234` and click on the **SIGN IN** button.
2. Click on the **NEW POST** button.
3. Choose a title for the blog post and add some content.
4. Click on the little arrow by the **SAVE DRAFT** button, choose **Publish Now** and click on **PUBLISH NOW** to confirm.

And that is the end of our user story for today.

### Save
The last step is to go back to the network tab, right-click any request and click on **Save as HAR with content**. This will save all the recorded requests into a [HAR file](https://en.wikipedia.org/wiki/.har) which we can now import into Loadmill.

## Import & Generalize
Once we have a recording of a user session, we are going to:

 1. **Import** the recording into Loadmill.
 2. **Remove** less interesting requests from the scenario.
 3. Perform a **Trial Run** and examine the output.
 4. Add **Parameters** to the test in order to use a data from previous requests in subsequent requests.
 5. **Repeat** The last two steps until we are satisfied with the result.
 
We start with going back to [Loadmill](https://www.loadmill.com) and opening a new test editor by clicking the **NEW TEST** link on the top navigation menu. We click the **IMPORT** button, select our HAR file and confirm.

**Note:** At this point you will be presented with a list of domains/hostnames used in the recording. In real life you will often see third party domains that are irrelevant to your test such as google analytics, Intercom, etc. If that happens, simply click the remove icon on the domains you want to filter out.

Once the import is complete, we see a list of all the requests made in the recorded user session - these requests will be played back in our test scenario.

The first is **POST** request for the login, followed by several **GET** requests for various resources, a **POST** request for creating the blog post, several **PUT** requests for adding the content and a final **PUT** request for publishing it.

In order to keep things nice and simple we remove everything except the login, creation and publish request (which contains the content as well).

![](/assets/del-reqs.gif)

### Running a trial test
Before we run a massive load test, we usually want to run just a single iteration of the scenario, to make sure everything works as expected. This is what we call a **Trial Run** or **Trial Test** (some like the term "dry run").

When we are creating a new test or extending/maintaining an old one, we like to iterate several times - modifying the test and trying it out - until we get the result we want.

To start a trial run, click the **TRY IT** button at the bottom of the editor. You will be promped to choose between running **remotely** (the default) or **locally**. There several good reasons to want to run locally, but for now we leave it on remote. 

![](/assets/Screen Shot 2017-11-02 at 10.37.16.png)

### Generalizing the test scenario
At this point the trial test should succeed, but our work is not yet done. There are two problems with this scenario, that would be clear to the person who designed the API, but to us may not be appearant at first glance:

1. The access token used in Request #2 and Request #3 is the one generated in the original session, and will expire within a few minutes. We need to use the authentication token provided in the response JSON to the login request instead.
2. Instead of publishing the blog post created by our scenario, it is the same one from the recorded session that will be published every time we run the test scenario.

This is to be expected, since the requests are executed exactly as they were recorded by the browser. However, with small modifications to our test scenario, we can **generalize** it so that it can be executed correctly multiple times and in parallel. We do that by using [Parametrization](parameters.html).

We start by fixing the login - we are going to create a **Parameter** named `access_token`, extract its value from the login response using [JSONPath](http://goessner.net/articles/JsonPath/) and use it to authenticate the other two requests. Let's do it step by step:
 
1. Click the **ADVANCED** button in the bottom-left corner of Request #1.
2. Expand the **Set Parameters** section by clicking it. 
3. Define a parameter named `access_token` and set the **JSONPath** query to  `$.access_token` or simply `access_token`. This parameter can now be used in subsequent requests.
![](/assets/Screen Shot 2017-11-02 at 13.59.02.png)

4. In the **Headers** section of Request #2, we find the **Authorization** header taken from the recording. It contains the access token from the recorded session - we replace it with the value of the parameter we have just created: `Bearer ${access_token}`. 
![](/assets/auth-header.png)

5. We do the same for Request #3.

Now every time we run the test scenario, the correct token is stored in our parameter and used in subsequent requests. We can run the trial again to verify this is indeed the case.

The second issue is solved similarly - we define parameters for the server-generated `postId` and `slug` from Request #2 and use them in Request #3. Let's do this step by step:

1. Set the parameter values for `postId` and `slug` with the JSONPath queries `posts[0].id` and `posts[0].slug`, respectively.
![](/assets/queries.png) 

2. This time we need to use our parametrs in the URL and request body of Request #3. This is done with the same syntax as before - we set the new URL to `https://loadmill-test-blog.herokuapp.com/ghost/api/v0.1/posts/${postId}/?include=tags` and set the values for the `id` and `slug` properties of the JSON request body to `"${postId}"` and `"${slug}"`, respectively.

![](/assets/params.gif) 