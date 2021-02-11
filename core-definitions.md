# Core definitions

## These are the key definitions that might help you get started:

#### **Test Plan**

[A Test Plan](https://docs.loadmill.com/api-testing/test-plan) is a set of Test Suites. A Test Plan run fails if one of its suites fails.

#### **Test Suite**

[A Test Suite](https://docs.loadmill.com/api-testing/test-suite-editor) is a set of test flows with shared configuration and [parameters](https://docs.loadmill.com/api-testing/test-suite-editor/parameters). A Test Suite run fails if one of its flows fails.

#### **Test Flow**

[A Test Flow](https://docs.loadmill.com/api-testing/test-suite-editor/test-flow-editor) is a set of HTTP requests & assertions running sequentially. A Test Flow run fails if one of its requests or assertion fails.

#### **Test Request**

[A Test Request](https://docs.loadmill.com/api-testing/test-suite-editor/request-editor) is the most basic building block of our tests. It represents a single API call or a user action. Requests can use parameters in their URL, body and headers fields.

#### **Default Parameter**

[A default parameter](https://docs.loadmill.com/api-testing/test-suite-editor/parameters#default-parameters) is a value used in a flow which is relevant to its execution context. I.e. target host, login credentials, and user input. 

Default parameters can be defined in the Test Suite parameters tab and used in requests using the template strings notation: `${parameter_name}`.

#### **Correlation**

A correlation between requests is a dynamic value which is the result of one request and is used in one or more of the following requests. I.e. a created entity ID used in the next request to update it. 

