---
description: Learn how to work with test configuration files
---

# Configuration Files

Loadmill test configuration files are an extension of the [HAR file format](https://en.wikipedia.org/wiki/.har). This test configuration example demonstrates some of the key elements such as - extractors, [assertions](assertions.md) and parameter defaults.

{% code-tabs %}
{% code-tabs-item title="example.json" %}
```javascript
{
    "duration": 600000,
    "concurrency": 125,
    "requests": [
        {
            "url": "https://loadmill-test-blog.herokuapp.com/ghost/api/v0.1/authentication/token/",
            "method": "POST",
            "headers": [],
            "assert": [],
            "extract": [ 
                {
                    "access_token": {
                        "jsonPath": "access_token"
                    }
                },
                {
                    "token_type": {
                        "jsonPath": "token_type"
                    }
                }
            ],
            "timeout": 22000,
            "description": "🚪 Login",
            "postData": {
                "text": "grant_type=password&username=a@b.com&password=Test1234&client_id=ghost-admin&client_secret=8c93bf1bb580",
                "mimeType": "application/x-www-form-urlencoded"
            },
            "delay": 1000
        },
        {
            "url": "https://loadmill-test-blog.herokuapp.com/ghost/api/v0.1/posts/",
            "method": "POST",
            "headers": [
                {
                    "Authorization": "${token_type} ${access_token}"
                }
            ],
            "assert": [
                {
                    "check": "postId"
                }
            ],
            "extract": [
                {
                    "postId": {
                        "jsonPath": "posts[0].id"
                    }
                }
            ],
            "timeout": 22000,
            "description": "📝   Create Post",
            "postData": {
                "text": "{\n   \"posts\": [\n      {\n         \"title\": \"Title ${__random_chars}\",\n         \"slug\": \"${__random_chars}\",\n         \"markdown\": \"Text ${__random_chars}\",\n         \"status\": \"published\"\n      }\n   ]\n}",
                "mimeType": "application/json"
            }
        }
    ],
    "meta": {
        "description": "Example test"
    },
    "parameters": [
        {
            "postText": "Test Post ${__random_chars}"
        },
        {
            "username": [
                "123",
                "456",
                "678"
            ]
        }
    ],
    "parameterPools": [],
    "targetedCountries": [],
    "iterationDelay": 2000,
    "cachePenetration": {
        "mode": "default"
    },
    "rampUp": 120000
}
```
{% endcode-tabs-item %}
{% endcode-tabs %}

