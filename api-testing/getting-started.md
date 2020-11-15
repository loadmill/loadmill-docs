---
description: Running your first API test.
---

# Getting Started

## These are the main key definitions that might help you get started:

**Test Suite**

A Test Suite is a set of test flows with shared configuration and [parameters](https://docs.loadmill.com/api-testing/test-suite-editor/parameters). A Test Suite run fails if one of its flows fails.

**Test Flow**

A Test Flow is a set of HTTP requests & assertions running sequentially. A Test Flow run fails if one of its requests or assertion fails.

**Test Request**

A Test Request is the most basic building block of our tests. It represents a single API call or a user action. Requests can use parameters in their URL, body and headers fields.

**Static Parameter**

A static parameter is a value used in a flow which is relevant to its execution context. I.e. target host, login credentials, and user input. 

Static parameters can be defined in the Test Suite parameters section and used in requests using the template strings notation: `${parameter_name}`.

**Correlation**

A correlation between requests is a dynamic value which is the result of one request and is used in one or more of the following requests. I.e. a created entity ID used in the next request to update it. 

