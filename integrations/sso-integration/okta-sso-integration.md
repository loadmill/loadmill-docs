# Okta SSO integration

Okta is an identity and access management service platform that allows to secure every identity, from customers to the workforce with Single Sign-On (SSO), Multi-factor Authentication and more.&#x20;

The Okta SSO integration with Loadmill enables Okta users to authenticate through Okta and then log into Loadmill without authenticating again.

### Configuration

**Requirements**

* Install the Loadmill application in your Okta instance
* Complete the steps below to set everything up

**Configuration steps**

After installing the application, you need to obtain some information that you will have to send to Loadmill

#### Gather information from Okta:

In the Okta admin page, click on the Loadmill application and then navigate to the General tab. Copy the following values:

* Client Id
* Client secret (click the eye button to toggle the visibility)
* Okta domain

**Send the information to Loadmill**

Once you have all the information (summarized below), email it to support@loadmill.com **:**

* Client Id
* Client secret (click the eye button to toggle the visibility)
* Okta domain
* Company email suffix (i.e. my-comany.com)

Loadmill support will handle your request and get back to you once the integration is configured.

#### Note

Loadmill - Okta SSO integration is limited to one email suffix per integration. Meaning that if, for example, your email is [jon@snow.com](mailto:jon@snow.com) and the email suffix you supplied to us was [snow.com](mailto:jon@snow.com) then this organization integration instance will support only email with that suffix.

### Authentication&#x20;

Once you've configured the integration with Okta, follow steps below to log into Loadmill:

Navigate to the [Login](https://app.loadmill.com/app/login) page => Click **SSO Log In**.

![](<../../.gitbook/assets/Screenshot (91).png>)

&#x20;Enter your email and click on the "SSO LOG IN"

![](<../../.gitbook/assets/image (50) (1).png>)

Choose the relevant account to login to

![](<../../.gitbook/assets/Screen Shot 2022-04-06 at 12.16.01.png>)

Enter your Okta credentials in the page you were redirected too.

![](<../../.gitbook/assets/image (52).png>)

In case, you are using Multi-Factor authentication, put the code you've got and click **Verify**.

![](<../../.gitbook/assets/Screen Shot 2022-01-03 at 14.48.52.png>)

That's it, you're in! 🎉&#x20;

### Support

We are always here if you need any help! Click on the bubble chat button in the lower-right corner of the screen or drop us a line at [support@loadmill.com](mailto:support@loadmill.com).
