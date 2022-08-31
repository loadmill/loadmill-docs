# Running Your API Test

Congrats! You managed to upload your test scenario to the Loadmill platform. Before running your test, let's walk through the key sections of your automated test.

#### **Naming Your Flow**

Naming your flow is (or should always be) your first step in creating and managing your automated test cases. It allows you to know what your flow is about and what should it do so never forget to name every flow/scenario you compose.

When uploading your flow/test scenario to Loadmill, you’ll see the flow added to your test suite on the left side of the app. By default, the name is the date and time you uploaded your test but make sure to rename it to, most commonly, the name of the operation you composed to a test.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2F2t1LeTvaYQ4Za9CHc1XM%2Frunning-1.mp4?alt=media&token=6a52489f-11ae-473e-a0c6-afbb3fd34434" %}

#### **Generated Test Code**

The generated test code from the scenario you registered is the most interesting part of Loadmill. After uploading your flow/scenario to Loadmill, its sophisticated AI generates a complete automated dynamic test build that you can easily view, edit and integrate. The generated code is located at the top of the editor and is written and saved in `.yaml`

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FM0EiRaIQChkdTSrNqBXQ%2Frunning-2.mp4?alt=media&token=70d1eb44-37a2-4cb5-825c-d2826c02a7b9" %}

#### API Components

From the generated automated test to your API components, Loadmill makes it easy for you to edit each API component related to your test case. Every component is expandable with various features such as extracting and validating dynamic values from the server response, running custom code to be used in each API call, and managing conditions for every API used for your test case.

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F-LHDbUNdi3wPd9vSolzU%2Fuploads%2FBwiVX8ctXyLSILf9lumc%2Frunning-3.mp4?alt=media&token=bf654d4f-952b-4bd9-bfe2-8d2ad6350a41" %}

#### **Running Your Test**

Loadmill offers multiple ways of running your test(s) like running your tests manually through the Loadmill app or running them through terminal but the most common one is the CI connection where, once connected to Loadmill, all you need to do is push your code to your CI and Loadmill will run the chosen tests automatically which gives you the freedom to concentrate more on your work rather than going through the hassle of managing multiple tabs and flows manually.
