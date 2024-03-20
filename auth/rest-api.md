---
description: >-
  Loadmill's API is an interface for interacting with Loadmill’s servers. Use it
  to create and launch your tests.
---

# REST API

Before getting started you’ll need to generate an API token, take a look how to generate it [here](https://docs.loadmill.com/integrations/api-tokens).

## Run Test Suite

<mark style="color:green;">`POST`</mark> `https://app.loadmill.com/api/v1/test-suites/:id/run`

Run a predefined test suite

#### Path Parameters

| Name | Type   | Description                    |
| ---- | ------ | ------------------------------ |
| id   | string | UUID of the Test Suite to run. |

#### Query Parameters

| Name          | Type    | Description                                                                                              |
| ------------- | ------- | -------------------------------------------------------------------------------------------------------- |
| forceAllFlows | boolean | Default = false - running only flows marked for execution with CI toggle. If true - executing all flows. |

#### Headers

| Name                                            | Type   | Description                                                                             |
| ----------------------------------------------- | ------ | --------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | string | Authentication token - you can generate it in the "User menu"> "Settings" > "Security". |

#### Request Body

| Name                  | Type   | Description                                                                                                                                                           |
| --------------------- | ------ | --------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| additionalDescription | string | Add an additional description at the end of the current suite's description                                                                                           |
| overrideParameters    | object | <p><code>name: value</code></p><p>pairs to override the default parameters values of this specific run. i.e.</p><p><code>{{"paramName1":"paramVal1"}, ...}</code></p> |

{% tabs %}
{% tab title="200 Test suite has launched successfully." %}
```
{testSuiteRunId: "running-uuid"}
```
{% endtab %}
{% endtabs %}

## Get Test Suite Run (Test Suite results)

<mark style="color:blue;">`GET`</mark> `https://app.loadmill.com/api/v1/test-suites-runs/:id`

Get a launched Test Suite results

#### Path Parameters

| Name | Type   | Description                                                                   |
| ---- | ------ | ----------------------------------------------------------------------------- |
| id   | string | The running uuid. You get this ID in the response when launching a Test Suite |

#### Headers

| Name          | Type   | Description                                                                            |
| ------------- | ------ | -------------------------------------------------------------------------------------- |
| Authorization | string | Authentication token - you can generate it in the "User menu"> "Settings" > "Security" |

{% tabs %}
{% tab title="200 " %}
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
{% endtab %}
{% endtabs %}

## Get Test Suite Flow Run

<mark style="color:blue;">`GET`</mark> `https://app.loadmill.com/api/v1/test-suites-runs/flows/:id`

Get Test Suite Flow results

#### Path Parameters

| Name | Type   | Description                                                                    |
| ---- | ------ | ------------------------------------------------------------------------------ |
| id   | string | The flow running uuid. You get this ID when fetching the Test Suite Run entity |

#### Headers

| Name          | Type   | Description                                                                            |
| ------------- | ------ | -------------------------------------------------------------------------------------- |
| Authorization | string | Authentication token - you can generate it in the "User menu"> "Settings" > "Security" |

{% tabs %}
{% tab title="200 " %}
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
{% endtab %}
{% endtabs %}

## Stop Test Suite Run

<mark style="color:orange;">`PUT`</mark> `https://app.loadmill.com/api/v1/test-suites-runs/:id`

Stop a launched Test Suite

#### Path Parameters

| Name | Type   | Description                                                                                                                                                                                          |
| ---- | ------ | ---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| id   | string | <p>The Test Suite Run uuid. You can get this ID in the response when getting the Test Suite Run (https://docs.loadmill.com/integrations/rest-api#get-test-suite-run-test-suite-results).</p><p>\</p> |

#### Query Parameters

| Name           | Type   | Description                                                                                |
| -------------- | ------ | ------------------------------------------------------------------------------------------ |
| forceFail=true | string | Using this filter option the user can stop the Test Suite Run and put its status to FAILED |

#### Headers

| Name          | Type   | Description                                                                            |
| ------------- | ------ | -------------------------------------------------------------------------------------- |
| Authorization | string | Authentication token - you can generate it in the "User menu"> "Settings" > "Security" |

#### Request Body

| Name                  | Type   | Description                                                |
| --------------------- | ------ | ---------------------------------------------------------- |
| additionalDescription | string | Will be added at the end of the Test Suite Run description |

{% tabs %}
{% tab title="200 Test Suite Run has been successfully stopped." %}
```
```
{% endtab %}
{% endtabs %}

## Create Load Test

<mark style="color:green;">`POST`</mark> `https://app.loadmill.com/api/v1/tests`

Create a load test from load test configuration

#### Headers

| Name          | Type   | Description                                                                            |
| ------------- | ------ | -------------------------------------------------------------------------------------- |
| Authorization | string | Authentication token - you can generate it in the "User menu"> "Settings" > "Security" |

#### Request Body

| Name   | Type   | Description                                                                                                                                                                                                          |
| ------ | ------ | -------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- |
| config | object | A load test configuration. The JSON test configuration may be exported from the Loadmill test editor or from an old test run. See a config example here - https://docs.loadmill.com/load-testing/configuration-files |

{% tabs %}
{% tab title="200 " %}
```
{ testId: "load test id" }
```
{% endtab %}
{% endtabs %}

## Set Flow

<mark style="color:purple;">`PATCH`</mark> `https://app.loadmill.com/api/v1/test-suites/:suiteId/flows/:flowId/pools`

Create a parameter pool and attach it to a flow

#### Path Parameters

| Name    | Type   | Description                                                     |
| ------- | ------ | --------------------------------------------------------------- |
| suiteId | string | The suite UUID in which the flow resides                        |
| flowId  | string | The flow UUID. The parameter pool will be attached to this flow |

#### Query Parameters

| Name | Type   | Description                     |
| ---- | ------ | ------------------------------- |
| name | string | name of the parameter pool data |

#### Headers

| Name          | Type   | Description                                                                            |
| ------------- | ------ | -------------------------------------------------------------------------------------- |
| content-type  | string | must be text/csv                                                                       |
| Authorization | string | Authentication token - you can generate it in the "User menu"> "Settings" > "Security" |

#### Request Body

| Name | Type   | Description                 |
| ---- | ------ | --------------------------- |
| body | string | The CSV data in CSV format. |

{% tabs %}
{% tab title="200 " %}
```
```
{% endtab %}
{% endtabs %}

## Run Load Test

<mark style="color:orange;">`PUT`</mark> `https://app.loadmill.com/api/v1/tests/:id/load`

Run an existing load test. Be aware that a given load test can be run only once. In order to rerun it you will have to recreate it.

#### Path Parameters

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| id   | string | Load test ID |

#### Headers

| Name          | Type   | Description                                                                            |
| ------------- | ------ | -------------------------------------------------------------------------------------- |
| Authorization | string | Authentication token - you can generate it in the "User menu"> "Settings" > "Security" |

{% tabs %}
{% tab title="200 " %}
```
```
{% endtab %}
{% endtabs %}

## Get Load Test

<mark style="color:blue;">`GET`</mark> `https://app.loadmill.com/api/v1/tests/:id`

Returns the Load Test data. If the Load Test has ended it would contain its result.

#### Path Parameters

| Name | Type   | Description  |
| ---- | ------ | ------------ |
| id   | string | Load test ID |

#### Headers

| Name          | Type   | Description                                                                            |
| ------------- | ------ | -------------------------------------------------------------------------------------- |
| Authorization | string | Authentication token - you can generate it in the "User menu"> "Settings" > "Security" |

{% tabs %}
{% tab title="200 " %}
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
{% endtab %}
{% endtabs %}

## Labels

<mark style="color:blue;">`GET`</mark> `https://app.loadmill.com/api/v1/labels`

Returns all user's team's labels

#### Query Parameters

| Name                             | Type   | Description                                                                                                 |
| -------------------------------- | ------ | ----------------------------------------------------------------------------------------------------------- |
| filter=active\&filter=evaluating | string | Using this filter option the user can get only the labels who are attached to flows with a specific status. |

#### Headers

| Name          | Type   | Description                                                                             |
| ------------- | ------ | --------------------------------------------------------------------------------------- |
| Authorization | string | Authentication token - you can generate it in the "User menu"> "Settings" > "Security". |

{% tabs %}
{% tab title="200 " %}
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
{% endtab %}
{% endtabs %}

## Run Test Plan

<mark style="color:green;">`POST`</mark> `https://app.loadmill.com/api/v1/test-plans/:test-plan-id/run`

Run a predefined test plan

#### Path Parameters

| Name                                           | Type   | Description                  |
| ---------------------------------------------- | ------ | ---------------------------- |
| test-plan-id<mark style="color:red;">\*</mark> | String | UUID of the Test Plan to run |

#### Headers

| Name                                            | Type   | Description                                                                             |
| ----------------------------------------------- | ------ | --------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Authentication token - you can generate it in the "User menu"> "Settings" > "Security". |

#### Request Body

| Name                  | Type   | Description                                                                                                                                                                                            |
| --------------------- | ------ | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------ |
| additionalDescription | String | Add an additional description at the end of the current plan's description                                                                                                                             |
| labels                | Array  | <p>An array of strings representing labels to filter the test plan execution. i.e. <code>["label1", "label2"]</code></p><p>Only test flows with matching labels will be included in the execution.</p> |
| labelsExpression      | String | String representing of labels expression to filter the test plan execution. i.e. `(label1 \| label2) & !label3` An expression may contain the characters `( ) & \| ! (`                                |
| overrideParameters    | Object | `name:value` pairs to override the default parameters values of this specific run. i.e. `{{"paramName1":"paramVal1"}, ...}`                                                                            |
| pool                  | String | Execute tests from a dedicated agent's pool (when using private agent)                                                                                                                                 |
| parallel              | String | Set the concurrency of a running test suites in a test plan. Max concurrency is 10                                                                                                                     |
| maxFlakyFlowRetries   | String | The maximum number of retries for flaky test flows. If a test flow fails due to flakiness, it will be retried up to the specified number of times                                                      |

{% tabs %}
{% tab title="200: OK return the an object with testPlanRunId property in it" %}

{% endtab %}
{% endtabs %}

## Get Test Plan Run

<mark style="color:blue;">`GET`</mark> `https://app.loadmill.com/api/v1/test-plans-runs/:plan-run-id`

Get the Test Plan Run result

#### Path Parameters

| Name                                               | Type   | Description                                           |
| -------------------------------------------------- | ------ | ----------------------------------------------------- |
| test-plan-run-id<mark style="color:red;">\*</mark> | String | test plan run id - given when launching the test plan |

#### Headers

| Name          | Type   | Description                                                                             |
| ------------- | ------ | --------------------------------------------------------------------------------------- |
| Authorization | String | Authentication token - you can generate it in the "User menu"> "Settings" > "Security". |

{% tabs %}
{% tab title="200: OK " %}

{% endtab %}
{% endtabs %}

## Re-run Test Plan

<mark style="color:green;">`POST`</mark> `https://app.loadmill.com/api/v1/test-plans-runs/:test-plan-run-id/re-run`

Re-run a test plan run

#### Path Parameters

| Name                                               | Type   | Description                         |
| -------------------------------------------------- | ------ | ----------------------------------- |
| test-run-plan-id<mark style="color:red;">\*</mark> | String | UUID of the Test Plan Run to re-run |

#### Query Parameters

| Name       | Type    | Description                                                                 |
| ---------- | ------- | --------------------------------------------------------------------------- |
| onlyFailed | boolean | Default = false. When set to true only failed or stopped suites will re-run |

#### Headers

| Name                                            | Type   | Description                                                                             |
| ----------------------------------------------- | ------ | --------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Authentication token - you can generate it in the "User menu"> "Settings" > "Security". |

{% tabs %}
{% tab title="200: OK return an object with testPlanRunId property in it" %}

{% endtab %}
{% endtabs %}

## Get test suites

<mark style="color:blue;">`GET`</mark> `https://app.loadmill.com/api/v1/test-suites`

Returns a list of test suites

#### Query Parameters

| Name        | Type   | Description                                                                |
| ----------- | ------ | -------------------------------------------------------------------------- |
| search      | String | filter test suites by the given search phrase                              |
| rowsPerPage | String | How many suites to return, Values might be `10, 25, 50, 100` default to 10 |

#### Headers

| Name                                            | Type   | Description                                                                             |
| ----------------------------------------------- | ------ | --------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Authentication token - you can generate it in the "User menu"> "Settings" > "Security". |

{% tabs %}
{% tab title="200: OK Returns an object with an array property of testSuites" %}

{% endtab %}
{% endtabs %}

## Get Test Plans

<mark style="color:blue;">`GET`</mark> `https://app.loadmill.com/api/v1/test-plans`

Returns a list of test plans

#### Query Parameters

| Name        | Type   | Description                                                                |
| ----------- | ------ | -------------------------------------------------------------------------- |
| search      | String | filter test suites by the given search phrase                              |
| rowsPerPage | String | How many suites to return, Values might be `10, 25, 50, 100` default to 10 |

#### Headers

| Name                                            | Type   | Description                                                                             |
| ----------------------------------------------- | ------ | --------------------------------------------------------------------------------------- |
| Authorization<mark style="color:red;">\*</mark> | String | Authentication token - you can generate it in the "User menu"> "Settings" > "Security". |
