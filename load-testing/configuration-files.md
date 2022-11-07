---
description: Learn how to work with test configuration files
---

# Configuration Files

Loadmill test configuration files are an extension of the [YAML file format](https://en.wikipedia.org/wiki/YAML). The test configuration example below was converted into JSON to be used in [our REST API](https://docs.loadmill.com/integrations/rest-api#create-load-test) and demonstrates some of the key elements such as - [extractions](https://docs.loadmill.com/api-testing/test-suite-editor/set-parameters-extractions), [assertions](../general/api-testing1/test-suite-editor/assertions.md) and parameter defaults.

{% code title="example.json" %}
```javascript
{
   "meta": {
      "description": "New Flow"
   },
   "requests": [
      {
         "description": "Basic flow",
         "method": "POST",
         "url": "httpbin.org/anything",
         "postData": {
            "text": "{\"parameter\":\"value\"}",
            "mimeType": "application/json"
         },
         "extract": [
            {
               "parameter_value": {
                  "jsonPath": "$.json.parameter"
               }
            }
         ],
         "assert": [
            {
               "check": "parameter_value"
            }
         ]
      }
   ],
   "parameters": [],
   "skipLoginFlow": true,
   "useCookies": true,
   "authenticationHeaders": [],
   "notifications": [],
   "concurrency": 50,
   "duration": 120000,
   "rampUp": 60000,
   "iterationDelay": 1000,
   "maxIterations": "5",
   "targetedCountries": []
}
```
{% endcode %}
