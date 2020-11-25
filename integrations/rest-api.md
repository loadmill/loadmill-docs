---
description: >-
  Loadmill's API is an interface for interacting with Loadmill’s servers. Use it
  to create and launch your tests.
---

# REST API

Before getting started you’ll need to generate an API token, take a look how to generate it  [here](https://docs.loadmill.com/integrations/api-tokens)

{% api-method method="post" host="https://www.loadmill.com/api" path="/v1/test-suites/:id/run" %}
{% api-method-summary %}
Run Test Suite
{% endapi-method-summary %}

{% api-method-description %}
Run a predefined test suite
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
UUID of the Test Suite to run. 
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Authentication token -  you can generate it in the "User menu"&gt; "Settings" &gt; "Security".
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="forceAllFlows" type="boolean" %}
Default = false - running only flows marked for execution with CI toggle. If true - executing all flows.
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="additionalDescription" type="string" required=false %}
Add an additional description at the end of the current suite's description
{% endapi-method-parameter %}

{% api-method-parameter name="overrideParameters" type="object" required=false %}
`name: value` pairs to override the default parameters values of this specific run. i.e. `{{"paramName1":"paramVal1"}, ...}`
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}
Test suite has launched successfully.
{% endapi-method-response-example-description %}

```
{testSuiteRunId: "running-uuid"}
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://www.loadmill/com" path="/api/v1/test-suites-runs/:id" %}
{% api-method-summary %}
Get Test Suite Run \(Test Suite results\)
{% endapi-method-summary %}

{% api-method-description %}
Get a launched Test Suite results 
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The running uuid. You get this ID in the response when launching a Test Suite
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Authentication token - you can generate it in the "User menu"&gt; "Settings" &gt; "Security"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://www.loadmill.com" path="/api/v1/test-suites-runs/flows/:id" %}
{% api-method-summary %}
Get Test Suite Flow Run
{% endapi-method-summary %}

{% api-method-description %}
Get Test Suite Flow results
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
The flow running uuid. You get this ID when fetching the Test Suite Run entity
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Authentication token - you can generate it in the "User menu"&gt; "Settings" &gt; "Security"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="post" host="https://www.loadmill.com" path="/api/v1/tests" %}
{% api-method-summary %}
Create Load Test
{% endapi-method-summary %}

{% api-method-description %}
Create a load test from load test configuration
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Authentication token - you can generate it in the "User menu"&gt; "Settings" &gt; "Security" 
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-body-parameters %}
{% api-method-parameter name="config" type="object" required=true %}
A load test configuration. The JSON test configuration may be exported from the Loadmill test editor or from an old test run. See a config example here - https://docs.loadmill.com/load-testing/working-with-the-test-editor/configuration-files
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```
{ testId: "load test id" }
```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="patch" host="https://www.loadmill.com" path="/api/v1/test-suites/:suiteId/flows/:flowId/pools" %}
{% api-method-summary %}
Set Flow's Parameter Pool
{% endapi-method-summary %}

{% api-method-description %}
Create a parameter pool and attach it to a flow
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="suiteId" type="string" required=true %}
The suite UUID in which the flow resides 
{% endapi-method-parameter %}

{% api-method-parameter name="flowId" type="string" required=true %}
The flow UUID. The parameter pool will be attached to this flow
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="content-type" type="string" required=true %}
must be text/csv
{% endapi-method-parameter %}

{% api-method-parameter name="Authorization" type="string" required=true %}
Authentication token - you can generate it in the "User menu"&gt; "Settings" &gt; "Security"
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="name" type="string" required=false %}
name of the parameter pool data
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}

{% api-method-body-parameters %}
{% api-method-parameter name="body" type="string" required=true %}
The CSV data in CSV format. 
{% endapi-method-parameter %}
{% endapi-method-body-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="put" host="https://www.loadmill.com" path="/api/v1/tests/:id/load" %}
{% api-method-summary %}
Run Load Test
{% endapi-method-summary %}

{% api-method-description %}
Run an existing load test. Be aware that a given load test can be run only once. In order to rerun it you will have to recreate it.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Load test ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Authentication token - you can generate it in the "User menu"&gt; "Settings" &gt; "Security" 
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

```

```
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://www.loadmill.com" path="/api/v1/tests/:id" %}
{% api-method-summary %}
Get Load Test
{% endapi-method-summary %}

{% api-method-description %}
Returns the Load Test data. If the Load Test has ended it would contain its result.
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-path-parameters %}
{% api-method-parameter name="id" type="string" required=true %}
Load test ID
{% endapi-method-parameter %}
{% endapi-method-path-parameters %}

{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Authentication token - you can generate it in the "User menu"&gt; "Settings" &gt; "Security"
{% endapi-method-parameter %}
{% endapi-method-headers %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

{% api-method method="get" host="https://www.loadmill.com/api" path="/v1/labels" %}
{% api-method-summary %}
Team's labels
{% endapi-method-summary %}

{% api-method-description %}
Returns all user's team's labels
{% endapi-method-description %}

{% api-method-spec %}
{% api-method-request %}
{% api-method-headers %}
{% api-method-parameter name="Authorization" type="string" required=true %}
Authentication token - you can generate it in the "User menu"&gt; "Settings" &gt; "Security".
{% endapi-method-parameter %}
{% endapi-method-headers %}

{% api-method-query-parameters %}
{% api-method-parameter name="filter=CI\_enabled" type="string" required=false %}
Using this filer option the user can get only the labels who are attached to flows with the CI toggle on
{% endapi-method-parameter %}
{% endapi-method-query-parameters %}
{% endapi-method-request %}

{% api-method-response %}
{% api-method-response-example httpCode=200 %}
{% api-method-response-example-description %}

{% endapi-method-response-example-description %}

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
{% endapi-method-response-example %}
{% endapi-method-response %}
{% endapi-method-spec %}
{% endapi-method %}

