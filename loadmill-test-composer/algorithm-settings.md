# Algorithm Configuration Guide

When creating a test in Loadmill, you can configure a rich set of rules that determine how your test scenario is analyzed, interpreted, and converted into an executable flow.
These settings control assertions, filtering, data cleanup, parameter extraction, uniqueness detection, and various advanced behaviors of the test-generation algorithm.

This guide explains every configuration option—what it does, when to use it, and how it affects the resulting test.

To apply or modify these configurations, go to the Algorithm page in Loadmill and click `Edit Algorithm Settings`

![](./../assets/algorithm-settings-ui.png)

And then edit or add the relevant rule in the correct JSON property

## Table of Contents
#### 1. Assertion Configuration
- [Assertions](#assertions)
- [Auto Assertions by URL](#auto-assertions-by-url)
- [Strict Response Validation](#strict-response-validation)
- [Automatic Polling by URL](#automatic-polling-by-url)

#### 2. Filtering & Control
- [Keep All MIME Types](#keep-all-mime-types)
- [Filter Irrelevant Requests](#filter-irrelevant-requests)
- [Filter Request by Body](#filter-request-by-body)
- [URL Blacklist](#url-blacklist)
- [Relevant URLs](#relevant-urls)
- [Headers Filters](#headers-filters)
- [Ignored Keys](#ignored-keys)
- [Ignored Values](#ignored-values)
- [Session Cut URLs](#session-cut-urls)
- [Irrelevant Soap Actions](#irrelevant-soap-actions)

#### 3. Data-cleanup
- [Reduce Global Parameters](#reduce-global-parameters)
- [Keep Original Values](#keep-original-values)
- [Don't Extract From Response by URL Regex](#dont-extract-from-response-by-url-regex)
- [Max Entities of Same Type](#max-entities-of-same-type)

#### 4. Structure & Semantics
- [Fields Hierarchy](#fields-hierarchy)
- [JSONPath Ignored Keys](#jsonpath-ignored-keys)
- [JQuery Ignored Elements](#jquery-ignored-elements)

#### 5. Parameter Detection
- [Search Unique Values](#search-unique-values)
- [Custom Uniqueness](#custom-uniqueness)
- [Non Secret Keys](#non-secret-keys)
- [Default Values](#default-values)
- [Value Holder Key Map](#value-holder-key-map)
- [Synonyms](#synonyms)
- [Special Keys](#special-keys)
- [Keys Value as Key](#keys-value-as-key)
- [Max Response Content Byte Size](#max-response-content-byte-size)
- [ResponseRegexExtractors](#response-regex-extractors)
- [Nested Value Decoding](#nested-value-decoding)
- [Custom Identifiers](#custom-identifiers)
- [Include Failed Requests](#include-failed-requests)

#### 6. Advanced & Serialization Settings

- [Array Format](#array-format)
- [Split Origin](#split-origin)
- [Allow Dots](#allow-dots)
- [Prettify Request Body](#prettify-request-body)
- [Decode URL Encoded Body](#decode-url-encoded-body)
- [Xml Decode](#xml-decode)

#### 7. Uniqueness & Extraction Controls
- [ID Prioritization](#id-prioritization)
- [Max Uniqueness Length](#max-uniqueness-length)

#### 8. Post Processing Editing
- [Yaml Regex Replacers](#yaml-regex-replacers)
- [Regex Replacers](#regex-replacers)
___

### Assertions
Defines **automatic assertions** that Loadmill applies to extracted parameters.
###### When to use:
- When your API contains stable response fields that should always be validated.
- When you want to detect silent failures (`200 OK` but the operation logically failed).

###### Structure:
*`assertions`* 
**Type:** array
**Description:**  A collection that defines how to generate assertions for extracted parameters

The object includes the following properties:
- *`isDefaultAssertion`*  
**Type:** boolean 
**Default:**  true
**Description:** Defines basic automatic assertions of *Exists* applied to all extracted parameters.

- *`specificAssertions`*
**Type:** array
**Default:** [ ]
**Description:** Define specific assertion applied to parameters with defined keys
Each item in the array contains:
  - *`key`*: 
      **Type:** string
      **Description:**  The key that, when encountered, should create the automatic assertion
  - *`assertion`*:  
      **Type:** `{ [assertionType: string]: string }`
      **Description:** Defines the assertion to apply.
      The object must contain a single assertion operator (e.g., equals, matches, contains) and its expected value.

Example:
```json
"assertions": {
  "isDefaultAssertion": true,
  "specificAssertions": [
    {
      "key": "success",
      "assertion": { "equals": "yes" }
    }
  ]
}
```

---
### Auto Assertions by URL 
Extracts a value from responses whose URL matches a pattern, then asserts it
###### When to use:
* When a specific endpoint always returns a value you want to verify.
###### Structure:
*`autoAssertionsByUrl`*
  **Type:** array
  **Description:** Defines automatic assertions for specific endpoints. Each item specifies a URL pattern, a JSONPath to extract the value, and the assertion to apply. 

Each item in the array contains:
  - *`url`*:  
    **Type:** string  
    **Description:** Regex pattern to match the request URL.

  - *`jsonpath`*:  
    **Type:** string  
    **Description:** JSONPath expression to extract the value from the response.

  - *`assertion`*:  
    **Type:** `{ [assertionType: string]: string }`  
    **Description:** Assertion operator and expected value (e.g., `{ "equals": "processed" }`).

Example:
```json
"autoAssertionsByUrl": [
  {
    "url": "/api/orders/[0-9]{8}$",
    "jsonpath": "$.data.status",
    "assertion": { "equals": "processed" }
  }
]
```
---
### Strict Response Validation
Defines **strict validation** rules for API responses using JSON Schema or "JSON contains" logic.

###### When to use:
- When your API response structure must be validated (schema-based testing).
- When responses contain dynamic values that shouldn't break validation (use `ignoreKeys`).

###### Structure:
*`strictResponseValidation`*
**Type:** object
**Description:** Controls whether Loadmill should automatically generate strict validation rules (JSON Schema or JSON Contains) for each API response.

The object includes the following properties:
- *`jsonSchema`*  
**Type:** boolean
**Default:** false
**Description:** Enables strict validation of the response against an auto-generated JSON Schema. Ensures the structure, types, and required fields match the expected schema.

- *`jsonContains`*  
**Type:** boolean  
**Default:** false  
**Description:** Enables validation that the response contains specific fields/values.

- *`ignoreKeys`*  
**Type:** array  
**Default:** [ ]
**Description:** A list of keys to exclude from validation. Useful for dynamic fields (e.g., id, timestamp, uuid) that change between runs.

- *`shouldValidateArrayItems`*  
**Type:** boolean  
**Default:** false  
**Description:** If true, validates each item in arrays individually.

Example:
```json
"strictResponseValidation": {
  "jsonSchema": true,
  "ignoreKeys": ["id"]
}
```

```json
"strictResponseValidation": {
  "jsonContains": true,
  "ignoreKeys": ["teamLabelsToIgnore", "name"],
  "shouldValidateArrayItems": true
}
```
---
### Automatic Polling by URL
Defines **automatic polling loops** for endpoints matching specific URL patterns.

###### When to use:
- When your system performs asynchronous operations requiring repeated polling.
- For status endpoints that eventually reach a final state.
- When testing processes that aren't instantaneous (e.g., onboarding, file processing).

###### Structure:

*`automaticLoops`*
**Type:** array
**Description:**  An array where each item defines the conditions under which an automatic loop should be added 

Each item in the array contains:
- *`url`*:  
  **Type:** string
  **Description:** Regex pattern to match the request URL.

- *`loop`*:  
  **Type:** object
  **Description:** Loop configuration.
    - *`iterations`*:  
      **Type:** number  
      **Description:** Number of polling attempts.
    - *`assert`*:  
      **Type:** `{ [assertionType: string]: string }`  
      **Description:** Assertion to apply on each polling response.
    - *`wait`*:  
      **Type:** number  
      **Description:** Wait time (ms) between iterations.

- *`expectedStatus`*:  
  **Type:** string  
  **Description:** Expected HTTP status code (e.g., `"ANY"`).

Example:
```json
"automaticLoops": [
  {
    "url": "https://example.com/orders/[0-9]{9}/status\\?subId=[0-9a-z]{40}",
    "loop": {
      "iterations": 20,
      "assert": { "check": "__status", "equals": "200" },
      "wait": 2000
    },
    "expectedStatus": "ANY"
  }
]
```
---
### Keep All MIME Types

Controls whether all MIME types are preserved during extraction.

###### When to use:
- When you need to extract parameters from non-standard or binary MIME types.
- To ensure no data is filtered out based on MIME type.

###### Structure:

*`keepAllMimeTypes`*  
**Type:** boolean  
**Default:** false  
**Description:** If true, all MIME types are kept during extraction, including binary and custom types.

Example:
```json
"keepAllMimeTypes": true
```
---
### Filter Irrelevant Requests
 Controls whether to automatically remove requests that don’t impact the outcome of the test, such as telemetry, health checks, and other noise.

###### When to use:
- When HAR contains a lot of browser noise (Mixpanel, GA, LinkedIn, etc.).
- When you want cleaner tests with fewer steps.
- When focusing only on business logic requests.

###### Structure:
*`filterIrrelevantRequests`*
**Type:** boolean  
**Default:** true  
**Description:** When enabled, the generated test is cleaner, more stable, and easier to debug.

Example:
```json
"filterIrrelevantRequests": true
```

---
### Filter Request by Body
Filters requests according to JSONPath rules.

###### When to use:
- When URL-based filtering is insufficient.
- When the request body is JSON.
- When the only reliable way to identify irrelevant requests is by inspecting the request body—for example, in GraphQL requests.

###### Structure:
*`filterRequestByBody`*
**Type:** array
**Description:** An array of filtering rules
Each item in the array contains:
- *`query`*:  
  **Type:** string  
  **Description:** JSONPath expression to match a value in the request body.
- *`equals`*:  
  **Type:** string  
  **Description:** Value to compare against the result of the JSONPath query.

Example:
```json
"filterRequestByBody": [
  {
    "query": "$.type",
    "equals": "telemetry"
  }
]
```
---
### URL Blacklist

Removes requests containing any of the specified substrings.
###### When to use
- To filter out entire domains.
- To eliminate 3rd-party scripts (CDN, tracking, ads).

###### Structure

*`urlBlackList`*
**Type:** string [ ]
**Description:** an array of substrings. Any request URL containing one of these substrings will be excluded from the generated test.


```json
{
  "urlBlackList": ["your-domain.com", "another-domain"]
}
```
### Relevant URLs
Forces these URLs not to be filtered.
###### When to use
* When your flow depends on URLs that look noisy but are actually important.
* To override aggressive filtering and ensure specific endpoints are always included.
###### Structure
*`relevantUrls`*
**Type:** string [ ]
**Description:** An array of URL substrings or patterns. Any request URL containing one of these will be included in the generated test, even if it would otherwise be filtered out.

Example:
```json
"relevantUrls": [
  "banking/sessions/create",
  "v1/cities"
]
```
---
### Headers Filters

Removes specific headers during processing.

###### When to use:
- To avoid extracting irrelevant or unstable headers.
- When headers contain high-frequency noise (Cloudflare, Chromium, WebSocket).
- When cleaning request data for readability.

###### Structure:

*`headersFilters`*  
**Type:** string [ ]  
**Description:** An array of header names or prefixes to exclude from extraction.

Example:
```json
"headersFilters": [
  "x-",
  "cf-",
  "accept",
  "Sec-WebSocket-Key",
  "cookie"
]
```
---

### Ignored Values

Skips extraction of trivial or unhelpful values.

###### When to use:
- To suppress useless values that appear frequently and create irrelevant parameters.

###### Structure:

*`ignoredValues`*  
**Type:** array  
**Default:** `["undefined", null, "null", true, "true", false, "false"]`  
**Description:** List of values to ignore during parameter extraction.

Example:
```json
"ignoredValues": ["undefined", null, "null", true, "true", false, "false"]
```
---
### Session Cut URLs

Defines URL patterns where a new session should be started during test generation.

###### When to use:
- When using a backend recordings.
- To split flows into distinct sessions for better isolation and analysis.

###### Structure:

*`sessionCutUrls`*  
**Type:** string [ ]  
**Description:** Array of URL substrings or regex patterns. When a request matches any of these, a new session is started.

Example:
```json
"sessionCutUrls": [
  "/api/login",
  "/logout"
]
```
---

### Irrelevant SOAP Actions

Filters out SOAP actions that should not be included in the generated test.

###### When to use:
- When your HAR contains SOAP requests with actions that are not relevant to your test scenario.
- To remove noise and focus on business-critical SOAP actions.

###### Structure:

*`irrelevantSoapActions`*  
**Type:** string [ ]  
**Description:** Array of SOAP action names to exclude from extraction and test generation.

Example:
```json
"irrelevantSoapActions": [
  "GetServerTime",
  "Ping"
]
```
---
### Reduce Global Parameters

Controls extraction of global parameters to prevent excessive or irrelevant parameterization.

###### When to use:
- When too many global parameters are being extracted, leading to noisy or unstable tests.
- To focus extraction only on meaningful parameters.

###### Structure:

*`reduceGlobalParameters`*  
**Type:** boolean  
**Default:** false  
**Description:** When enabled, limits extraction of global parameters to only those that are relevant.

Example:
```json
"reduceGlobalParameters": true
```
---
#### Keep Original Values
Prevents extraction for matching URLs.
###### When to use:
- When there are fixed values that you don't want to replace with parameters.

###### Structure:
*`keepOriginalValues`*
**Type:** string [ ]  
**Description:** Array of URL patterns for which values should not be replaced with parameters.

Example:
```json
"keepOriginalValues": ["/internal/status"]
```
---

### Don\'t Extract From Response by URL Regex
Skips extraction for responses whose request URL matches a pattern.
###### When to use:
- When some endpoints return noisy or irrelevant payloads.

###### Structure:
*`dontExtractFromResponseByURLRegex`*
**Type:** string [ ]  
**Description:** Array of regex patterns. Extraction is skipped for responses matching these patterns.

Example:
```json
"dontExtractFromResponseByURLRegex": ["pattern1", "pattern2"]
```
---
### Max Entities of Same Type
Limits how many identical keys are extracted from a single request.
###### When to use
- When responses include many repetitive objects.

###### Structure:
*`maxEntitiesOfSameType`*
**Type:** number  
**Default:** 15
**Description:** Maximum number of identical keys to extract per request.

Example:
```json
"maxEntitiesOfSameType": 15
```
---
### Fields Hierarchy

Defines how extracted JSONPaths use attribute-based selectors instead of index-based selectors for improved stability.

###### When to use:
- When the entity type can be reliably identified by a specific key.
- To avoid unstable extraction paths that depend on array indices.

###### Structure:

*`fieldsHierarchy`*  
**Type:** string [ ]  
**Description:** Array of field names. When present, extraction paths will use attribute-based selectors for these fields.

Example:
```json
"fieldsHierarchy": ["name", "title"]
```
---
### JSONPath Ignored Keys

Defines patterns for dynamic key segments (such as UUIDs or timestamps) that should be replaced with recursive descent (`..`) in generated JSONPath expressions, improving stability.

###### When to use:
- When dynamic map keys (such as UUIDs or timestamps) make JSONPath expressions unstable.
- To simplify extraction paths and avoid brittle selectors.

###### Structure:

*`jsonpathIgnoredKeys`*  
**Type:** string [ ]  
**Description:** Array of regex patterns. Any key matching a pattern will be replaced with recursive descent in JSONPath.

Example:
```json
"jsonpathIgnoredKeys": [
  "^[0-9a-fA-F]{8}-[0-9a-fA-F]{4}-4[0-9a-fA-F]{3}-[89abAB][0-9a-fA-F]{3}-[0-9a-fA-F]{12}$"
]
```
---
### jQuery Ignored Elements

Skips extraction for specific HTML elements when generating jQuery selectors.

###### When to use:
- When invalid HTML causes Loadmill to fix the markup and generate selectors on the corrected structure.
- When you want to avoid extracting or interacting with certain elements, even after HTML correction.

###### Structure:

*`jqueryIgnoredElements`*  
**Type:** string [ ]  
**Description:** Array of HTML element names to ignore during jQuery selector generation.

Example:
```json
"jqueryIgnoredElements": ["tbody"]
```
---
### Search Unique Values

Detects unique values and their reoccurrences based on their values, not just their keys or context.

###### When to use:
- When you want to identify unique values according to their actual content, regardless of their field names or context.

###### Structure:

*`searchUniqValues`*  
**Type:** boolean  
**Default:** false  
**Description:** When enabled, the algorithm will detect and correlate unique values wherever they appear.

Example:
```json
"searchUniqValues": true
```
---
### Custom Uniqueness

Detects unique values and their reoccurrences by specifying keys and regex patterns. Without any additional conditions.

###### When to use:
- When a key contains a unique and important value that should be replaced everywhere it appears.

###### Structure:
*`customUniqueness`*
**Type:** array
**Description:** An array where each item contains rules that define unique values

Each item in the array contains:
- *`key`*:  
  **Type:** string  
  **Description:** The key whose value should be detected as unique.
- *`regex`*:  
  **Type:** string  
  **Description:** Regex pattern to match the unique value.

Example:
```json
"customUniqueness": [
  {
    "key": "patientNumber",
    "regex": "^[a-z0-9]{25}$"
  }
]
```
---
### Non-Secret Keys

Defines keys whose values are considered non-sensitive and will be extracted and recorded even when operating in secure mode.

###### When to use:
- When using a backend recordings.
- When you want to ensure certain values are always extracted, even in secure recording.
- When specific keys do not contain secrets and should be included for correlation or debugging.

###### Structure:

*`nonSecretKeys`*  
**Type:** string [ ]  
**Description:** Array of key names whose values are safe to extract and record.

Example:
```json
"nonSecretKeys": ["sessionId", "userId"]
```
---
### Default Values

Assigns fallback values to specific fields during test generation.

###### When to use:
- When you need to extract a specific value from the request body and create correlations for it.
- When fixed values must be replaced with dynamic ones (e.g., timestamps, dates, random IDs).

###### Structure:
*`defaultValues`*
**Type:** array
**Description:** an array where each item contains rules that define how to extract parameters and assign them a default value.

Each item in the array contains:
- *`selector`*:  
  **Type:** string  
  **Description:** The key to identify the field.
- *`value`*:  
  **Type:** string  
  **Description:** The fallback value to assign.
- *`name`*:  
  **Type:** string  
  **Description:** The parameter name to use for correlation.

Example:
```json
"defaultValues": [
  {
    "selector": "userId",
    "value": "123",
    "name": "userId"
  }
]
```  
---
### Value Holder Key Map

Extracts nested values when a key contains an object instead of a primitive.

###### When to use:
- When a field stores a nested object instead of a primitive.

###### Structure:
*`valueHolderKeyMap`*
**Type:** array 
**Description:** an array where each item contains rules for extracting parameters whose value is located inside one of their nested fields.

Each item in the array contains:
- *`containerKey`*:  
  **Type:** string  
  **Description:** The key whose value is an object containing the actual value.
- *`valueKey`*:  
  **Type:** string  
  **Description:** The key inside the object that holds the value to extract.

Example:
```json
"valueHolderKeyMap": [
  { "containerKey": "password", "valueKey": "text" },
  { "containerKey": "id", "valueKey": "value" }
]
```
---
### Synonyms

Maps different key names to unify correlation and extraction.

###### When to use:
- When different endpoints use different naming conventions for the same logical identifier.
- To unify extraction and correlation of values across APIs with inconsistent field names.

###### Structure:

*`synonyms`*  
**Type:** array  
**Default:** [ ]  
**Description:** Each item is an array of key names that should be treated as synonyms for correlation and extraction.

Example:
```json
"synonyms": [
  ["sku", "product"],
  ["amountPaid", "totalAmountPaid", "totalAmount"],
  ["customerQuoteTime", "delivery"]
]
```
---
### Special Keys

Always extracts these keys from the request body, regardless of other extraction settings.

###### When to use:
- When `reduceGlobalParameters` is off and you still want to extract certain keys from the request body.

###### Structure:

*`specialKeys`*  
**Type:** string [ ]  
**Description:** Array of key names to always extract from the request body.

Example:
```json
"specialKeys": [
  "totalAmount", "delivery", "customerQuoteTime", "subtotalAmount"
]
```
---
### Keys Value as Key

Treats the value of a key as a parameter.

###### When to use:
- When you need to extract a value from a key and use it as a parameter for correlation or substitution.

###### Structure:

*`keysValueAsKey`*  
**Type:** string [ ]  
**Description:** Array of key names whose values should be treated as parameters.

Example:
```json
"keysValueAsKey": ["customTokenField"]
```
---
### Max Response Content Byte Size

Controls the maximum response size (in bytes) that the system will process for parameter extraction.

###### When to use:
-  Increase the default value when you need to extract parameters from very large responses.

###### Structure:

*`maxResponseContentByteSize`*  
**Type:** number  
**Default:** 250000
**Description:** Maximum response size (in bytes) that will be processed for extraction.

Example:
```json
"maxResponseContentByteSize": 250000
```
---
### Response Regex Extractors

Extracts values from response bodies using regex capturing groups.

###### When to use:
- When you need to extract and correlate a value from the response body that cannot be accessed using standard extraction methods (e.g., not available via JSONPath).

###### Structure:
*`responseRegexExtractors`*
**Type:** array  
**Description:** an array where each item contains rules for extracting parameters from the response body using regex.

Each item in the array contains:
- *`regex`*:  
  **Type:** string  
  **Description:** Regex pattern with capturing groups to extract the desired value from the response body.
- *`name`*:  
  **Type:** string  
  **Description:** The parameter name to assign to the extracted value.
- *`forceExtract`*:  
  **Type:** boolean  
  **Default:** false  
  **Description:** If true, always extract the value even if it only appears once and has no correlations.

Example:
```json
"responseRegexExtractors": [
  {
    "name": "refresh_token_id",
    "forceExtract": false
  }
]
```
---
### Nested Value Decoding

Parses and extracts parameters from fields containing stringified JSON objects.

###### When to use:
- When a field contains a stringified JSON object that needs to be parsed for parameter extraction and correlation.

###### Structure:
*`nestedValueDecoding`*
**Type:** array
**Description:** an array where each item contains rules specifying which keys in the response body should undergo additional parsing.

Each item in the array contains:
- *`key`*:  
  **Type:** string  
  **Description:** The key whose value is a stringified JSON object.
- *`type`*:  
  **Type:** string  
  **Description:** The format of the nested value (e.g., `"JSON"`).

Example:
```json
"nestedValueDecoding": [
  {
    "key": "value",
    "type": "JSON"
  }
]
```
---
### Custom Identifiers

Adds custom identifier field names (case-insensitive) for parameter extraction.

###### When to use:
- When your system uses nonstandard naming for ID fields.
- To ensure custom identifier fields are prioritized during extraction and correlation.

###### Structure:

*`customIdentifiers`*  
**Type:** string [ ]  
**Description:** Array of field names (case-insensitive) to treat as identifiers during extraction.

Example:
```json
"customIdentifiers": ["testSuiteCard", "orderNumber"]
```
---
### Include Failed Requests

Includes failed HTTP requests in the generated test.

###### When to use:
- For debugging flows where failures are expected or important.
- When you want to analyze and reproduce error scenarios.

###### Structure:

*`includeFailedRequests`*  
**Type:** boolean  
**Default:** false  
**Description:** When enabled, failed HTTP requests (non-2xx responses) are included in the generated test.

Example:
```json
"includeFailedRequests": true
```
---
### Array Format

Controls how arrays are serialized in URL-encoded form.

###### When to use:
- When URL-encoded arrays must follow a specific backend format.
- To ensure compatibility with server-side array parsing.

###### Structure:

*`arrayFormat`*  
**Type:** string  
**Allowed values:** "indices" | "brackets" | "repeat"
**Default:** "indices"
**Description:** Specifies the serialization format for arrays in URL-encoded bodies.

Example:
```json
"arrayFormat": "indices"
```
---
### Split Origin

Separates origins into host and protocol components.

###### When to use:
- When combining HAR files from backend recordings.
- To ensure requests are grouped and processed by their actual origin.

###### Structure:

*`splitOrigin`*  
**Type:** boolean  
**Default:** false  
**Description:** If enabled, splits the origin into host and protocol for more granular processing.

Example:
```json
"splitOrigin": false
```
---
### Allow Dots

Controls whether dots (`.`) are allowed in parameter names.

###### When to use:
- When parameter names may safely contain dots (e.g., `user.name`).
- To support APIs or systems that use dotted notation for keys.

###### Structure:

*`allowDots`*  
**Type:** boolean  
**Default:** false  
**Description:** If true, allows dots in parameter names during extraction and correlation.

Example:
```json
"allowDots": false
```  
---
### Prettify Request Body

Controls formatting of request bodies in the generated YAML output.

###### When to use:
- When you want readable, formatted JSON bodies in your test output.
- When performance snapshots require compact bodies (disable prettification).

###### Structure:

*`prettifyRequestBody`*  
**Type:** boolean  
**Default:** true  
**Description:** If true, pretty-prints large JSON bodies in output YAML for readability. If false, leaves request bodies compact (not formatted).

Example:
```json
"prettifyRequestBody": true
```
---
### Decode URL-Encoded Body

Enables decoding of request bodies with `application/x-www-form-urlencoded` content type.

###### When to use:
- For POST requests with `application/x-www-form-urlencoded`.
- When you need to extract parameters from URL-encoded request bodies.

###### Structure:

*`decodeUrlEncodedBody`*  
**Type:** boolean  
**Default:** false  
**Description:** If true, decodes URL-encoded request bodies for parameter extraction.

Example:
```json
"decodeUrlEncodedBody": true
```
---
### XML Decode

Enables decoding of special formats from systems like Priority ERP (not standard XML).

###### When to use:
- When working with Priority ERP or systems returning non-standard XML encodings.

###### Structure:

*`xmlDecode`*  
**Type:** boolean  
**Default:** false  
**Description:** If true, enables decoding and extraction from non-standard XML formats.

Example:
```json
"xmlDecode": true
```
---
### ID Prioritization

Prioritizes extraction of parameters whose keys match known or custom identifier fields (such as `id`, `uuid`, or those defined in `customIdentifiers`) when multiple candidates exist in an object or array.

###### When to use:
- When your data contains multiple possible identifiers and you want to ensure the most meaningful one is extracted.
- To improve correlation and stability by always preferring standard or custom ID fields.

###### Structure:

*`idPrioritization`*  
**Type:** boolean  
**Default:** false  
**Description:** If true, extraction will prioritize keys matching identifier fields (e.g., `id`, `uuid`, or those in `customIdentifiers`) over other candidates.

Example:
```json
"idPrioritization": false
```
---
### Max Uniqueness Length

Limits the maximum length of a value considered for uniqueness detection.

###### When to use:
- To avoid extracting long strings (such as logs, SQL queries, or HTML) as parameters.
- When you want to prevent noisy or irrelevant values from being treated as unique identifiers.

###### Structure:

*`maxUniquenessLength`*  
**Type:** number  
**Default:**  40
**Description:** Maximum length (in characters) of a value to be considered for uniqueness detection. Values longer than this will be ignored.

Example:
```json
"maxUniquenessLength": 40
```
---
### YAML Regex Replacers

post-processing regex replacements on the generated YAML output.

###### When to use:
- When you need to mask, transform, or enhance YAML after generation.

###### Structure:

*`yamlRegexReplacers`*
**Type:** array
**Description:** an array where each item contains rules specifying which changes should be applied to the generated YAML.

Each item in the array contains:
- *`regex`*:  
  **Type:** string  
  **Description:** Regex pattern to match in the YAML output.
- *`replace`*:  
  **Type:** string  
  **Description:** Replacement string to substitute for matches.
- *`flags`*:  
  **Type:** string  
  **Default:** ""
  **Description:** Regex flags (e.g., `"g"` for global, `"i"` for case-insensitive).

Example:
```json
"yamlRegexReplacers": [
  {
    "regex": "password: \".*\"",
    "replace": "password: \"***\"",
    "flags": "g"
  }
]
```
---
### Regex Replacers

Extracts values from requests using regex capturing groups.

###### When to use:
- When values do not appear in JSON at all (e.g., tokens inside headers or raw bodies).
- When there is a repeated value that was not extracted into a parameter.

###### Structure:

*`regexReplacers`*
**Type:** array
**Description:** an array where each item contains a regex that, if matched, should create a parameter for it.
Each item in the array contains:
- *`name`*:  
  **Type:** string  
  **Description:** The parameter name to assign to the extracted value.
- *`regex`*:  
  **Type:** string  
  **Description:** Regex pattern with capturing groups to extract the desired value from the request.
- *`reuse`*:  
  **Type:** boolean  
  **Default:** false  
  **Description:** If true, reuses an existing parameter even when the values are different.

Example:
```json
"regexReplacers": [
  {
    "name": "auth_token",
    "regex": "eyJhbGciOi.*",
    "reuse": true
  }
]
```
---