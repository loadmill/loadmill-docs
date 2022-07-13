---
description: >-
  Loadmill's API is an interface for interacting with Loadmill’s servers. Use it
  to create and launch your tests.
---

# REST API

Before getting started you’ll need to generate an API token, take a look how to generate it [here](https://docs.loadmill.com/integrations/api-tokens).

{% swagger baseUrl="https://app.loadmill.com/api" path="/v1/test-suites/:id/run" method="post" summary="Run Test Suite" %}
{% swagger-description %}
Run a predefined test suite
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="string" required="false" %}
UUID of the Test Suite to run.
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="false" %}
Authentication token - you can generate it in the "User menu"> "Settings" > "Security".
{% endswagger-parameter %}

{% swagger-parameter in="query" name="forceAllFlows" type="boolean" required="false" %}
Default = false - running only flows marked for execution with CI toggle. If true - executing all flows.
{% endswagger-parameter %}

{% swagger-parameter in="body" name="additionalDescription" type="string" required="false" %}
Add an additional description at the end of the current suite's description
{% endswagger-parameter %}

{% swagger-parameter in="body" name="overrideParameters" type="object" required="false" %}
`name: value`

pairs to override the default parameters values of this specific run. i.e.

`{{"paramName1":"paramVal1"}, ...}`
{% endswagger-parameter %}

{% swagger-response status="200" description="Test suite has launched successfully." %}
```
{testSuiteRunId: "running-uuid"}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://app.loadmill.com" path="/api/v1/test-suites-runs/:id" method="get" summary="Get Test Suite Run (Test Suite results)" %}
{% swagger-description %}
Get a launched Test Suite results
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="string" required="false" %}
The running uuid. You get this ID in the response when launching a Test Suite
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="false" %}
Authentication token - you can generate it in the "User menu"> "Settings" > "Security"
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "id": "test suite run uuid,
  "description": "test suite run description",
  "startTime": timestamp,
  "endTime": timestamp | null,
  "conf": {
    "useCookies": true
  },
  "status": "PASSED" | "FAILED" | "RUNNING",
  "displayName": "Display name of the executing user",
  "testSuiteId": "origin test suite uuid" | null (if deleted),
  "testSuiteFlowRuns": [
    {
      "id": "test suite flow run uuid",
      "startTime": timestamp,
      "endTime": timestamp | null,
      "conf": {}, // executed flow conf 
      "description": "Flow description",
      "status": "PASSED" | "FAILED" | "RUNNING",
      "numOfRequests": number of requests in this flow conf,
      "avgResTime": 199, // in ms
      "duration": "422 ms"
    }
  ],
  "progress": "1/1", // flows progress
  "successRate": "100%", // flows success rate
  "avgResTime": "422 ms"
} 
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://app.loadmill.com" path="/api/v1/test-suites-runs/flows/:id" method="get" summary="Get Test Suite Flow Run" %}
{% swagger-description %}
Get Test Suite Flow results
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="string" required="false" %}
The flow running uuid. You get this ID when fetching the Test Suite Run entity
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="false" %}
Authentication token - you can generate it in the "User menu"> "Settings" > "Security"
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "id": "test suite flow run uuid",
  "description": "Flow description",
  "conf": {...}, // the executed flow conf
  "status": "PASSED" | "FAILED" | "RUNNING",
  "startTime": timestamp,
  "testSuiteFlowId": "origin test suite flow uuid" | null (if deleted),
  "testSuiteId": "origin test suite uuid" | null (if deleted)
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://app.loadmill.com" path="/api/v1/test-suites-runs/:id" method="put" summary="Stop Test Suite Run" %}
{% swagger-description %}
Stop a launched Test Suite
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="string" required="false" %}
The Test Suite Run uuid. You can get this ID in the response when getting the Test Suite Run (https://docs.loadmill.com/integrations/rest-api#get-test-suite-run-test-suite-results).

\\
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="false" %}
Authentication token - you can generate it in the "User menu"> "Settings" > "Security"
{% endswagger-parameter %}

{% swagger-parameter in="query" name="forceFail=true" type="string" required="false" %}
Using this filter option the user can stop the Test Suite Run and put its status to FAILED
{% endswagger-parameter %}

{% swagger-parameter in="body" name="additionalDescription" type="string" %}
Will be added at the end of the test suite description
{% endswagger-parameter %}

{% swagger-response status="200" description="Test Suite Run has been successfully stopped." %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://app.loadmill.com" path="/api/v1/tests" method="post" summary="Create Load Test" %}
{% swagger-description %}
Create a load test from load test configuration
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="false" %}
Authentication token - you can generate it in the "User menu"> "Settings" > "Security"
{% endswagger-parameter %}

{% swagger-parameter in="body" name="config" type="object" required="false" %}
A load test configuration. The JSON test configuration may be exported from the Loadmill test editor or from an old test run. See a config example here - https://docs.loadmill.com/load-testing/configuration-files
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{ testId: "load test id" }
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://app.loadmill.com" path="/api/v1/test-suites/:suiteId/flows/:flowId/pools" method="patch" summary="Set Flow" %}
{% swagger-description %}
Create a parameter pool and attach it to a flow
{% endswagger-description %}

{% swagger-parameter in="path" name="suiteId" type="string" required="false" %}
The suite UUID in which the flow resides
{% endswagger-parameter %}

{% swagger-parameter in="path" name="flowId" type="string" required="false" %}
The flow UUID. The parameter pool will be attached to this flow
{% endswagger-parameter %}

{% swagger-parameter in="header" name="content-type" type="string" required="false" %}
must be text/csv
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="false" %}
Authentication token - you can generate it in the "User menu"> "Settings" > "Security"
{% endswagger-parameter %}

{% swagger-parameter in="query" name="name" type="string" required="false" %}
name of the parameter pool data
{% endswagger-parameter %}

{% swagger-parameter in="body" name="body" type="string" required="false" %}
The CSV data in CSV format.
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://app.loadmill.com" path="/api/v1/tests/:id/load" method="put" summary="Run Load Test" %}
{% swagger-description %}
Run an existing load test. Be aware that a given load test can be run only once. In order to rerun it you will have to recreate it.
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="string" required="false" %}
Load test ID
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="false" %}
Authentication token - you can generate it in the "User menu"> "Settings" > "Security"
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://app.loadmill.com" path="/api/v1/tests/:id" method="get" summary="Get Load Test" %}
{% swagger-description %}
Returns the Load Test data. If the Load Test has ended it would contain its result.
{% endswagger-description %}

{% swagger-parameter in="path" name="id" type="string" required="false" %}
Load test ID
{% endswagger-parameter %}

{% swagger-parameter in="header" name="Authorization" type="string" required="false" %}
Authentication token - you can generate it in the "User menu"> "Settings" > "Security"
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "id": "load test id",
  "startTime": timestamp,
  "endTime": timestamp,
  "usedSeconds": "total seconds used by all sessions",
  "description": "load description",
  "conf": {}, // load test configuraion
  "result": "aborted" | "done" | "failed",
  "failedIterations": number,
  "successfulIterations": number
}
```
{% endswagger-response %}
{% endswagger %}

{% swagger baseUrl="https://app.loadmill.com/api" path="/v1/labels" method="get" summary="Team" %}
{% swagger-description %}
Returns all user's team's labels
{% endswagger-description %}

{% swagger-parameter in="header" name="Authorization" type="string" required="false" %}
Authentication token - you can generate it in the "User menu"> "Settings" > "Security".
{% endswagger-parameter %}

{% swagger-parameter in="query" name="filter=CI_enabled" type="string" required="false" %}
Using this filter option the user can get only the labels who are attached to flows with the CI toggle on
{% endswagger-parameter %}

{% swagger-response status="200" description="" %}
```
{
  "teamLabels": [
    {
      "id": "123e4567-e89b-12d3-a456-426614174001",
      "description": "my label",
    },
    {
      "id": "123e4567-e89b-12d3-a456-426614174002",
      "description": "another label",
    }
  ]
}
```
{% endswagger-response %}
{% endswagger %}
