---
description: Running API and Load tests locally or on your servers.
---

# Loadmill Agent

Running API and load tests locally on your own servers can offer several benefits, including faster test execution, greater control over the testing environment, improved isolation of issues, and enhanced security.&#x20;

By running tests locally, you can avoid the latency and potential security risks associated with sending requests over the internet, and have more control over the testing environment to simulate different conditions and more effectively identify and fix issues with your API or application.

The Loadmill Agent is a tool that enables you to run load and performance tests on your servers or local environment. It acts as a proxy, intercepting requests made to your API or application and forwarding them to the Loadmill testing platform. The Loadmill Agent can be installed on your servers or locally on your development machine and configured to intercept requests made to specific endpoints or domains.

You can download the Loadmill agent via npm package or use our newly release desktop app for macOS.

### MacOS Desktop App

Loadmill has recently released a new desktop app for macOS that allows users to perform regular and local testing using a private agent. The app is designed to be easy to use and provides a convenient way to access Loadmill's powerful testing capabilities from a Mac computer.

One of the key features of the app is the private agent, which allows users to conduct testing on their own devices without having to rely on external servers. This is particularly useful for local testing, as it allows users to test their applications in a controlled environment without having to worry about network connectivity or other external factors.

To use the private agent, users will need to generate a Loadmill [security token](https://app.loadmill.com/app/user/settings/security). Once the token has been generated, it can be used to authenticate the private agent and begin testing.

{% tabs %}
{% tab title="Agent Installation" %}
{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F2vjiLjsWmvQaVMxaG2Eb%2Fuploads%2FQDUMs5rV3mIhpyZXbbnJ%2Fmacos-agent-installation.mp4?alt=media&token=ba4a835c-5379-40b5-b28a-21e6b35886e7" %}
{% endtab %}

{% tab title="Agent Run" %}
{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F2vjiLjsWmvQaVMxaG2Eb%2Fuploads%2FmL4BekLzpYnjwNrHKlXf%2Fmacos-agent-run.mp4?alt=media&token=552931e4-1a8c-4ace-b18e-311012ef9fb3" %}
{% endtab %}
{% endtabs %}

### NPM Package/Docker Installation

Run the following command if you have Docker installed on your machine:

`docker run -it --rm -e LOADMILL_AGENT_TOKEN=<your-api-token> loadmill/agent`

For more information, please [click here](https://hub.docker.com/r/loadmill/agent)

#### NPM Package

**Prerequisites**

1. Node version 14 or higher installed.
2. [Generated Token](https://docs.loadmill.com/integrations/api-tokens)

**Installation**

<table><thead><tr><th width="439">using npm</th><th>using yarn</th></tr></thead><tbody><tr><td><p><code>npm i @loadmill/agent -g</code></p><p><code>npm i @loadmill/agent // in case you can't install it globally.</code> </p></td><td><code>yarn add @loadmill/agent -g</code></td></tr></tbody></table>

#### Running the Agent

| installed globally (-g)           | installed locally                                                    |
| --------------------------------- | -------------------------------------------------------------------- |
| `loadmill-agent start -t <token>` | `./node_modules/@loadmill/agent/bin/loadmill-agent start -t <token>` |

{% embed url="https://files.gitbook.com/v0/b/gitbook-x-prod.appspot.com/o/spaces%2F2vjiLjsWmvQaVMxaG2Eb%2Fuploads%2FDkvD3iwOZNnJvVb6QMBd%2Fterminal-agent-run.mp4?alt=media&token=9bdb391f-c155-4190-93a1-ffacb87430cd" %}

#### Commands

The start command accepts the following options:

* `--token` - (REQUIRED) can be retrieved [through the UI](https://docs.loadmill.com/integrations/api-tokens).
* `--loads-capacity` - (default = 50). Optionally you can supply the number of users this agent can simulate. It can be 0 in order not to run load tests.
* `--no-api` - can be supplied in order to run [Load tests](https://docs.loadmill.com/load-testing/getting-started) only, [API tests](https://docs.loadmill.com/api-testing/getting-started) will run on Loadmill servers.
* `--pool` - can be supplied in order to set the agent pool (the limit is 256 characters). When using multiple Loadmill Agents, this parameter helps you distinguish between running agents. Then, use [our npm module](https://www.npmjs.com/package/loadmill) with supplying the `--pool <pool>` parameter to assign test runs to a specific agent.
* `--config` - alternatively, you can supply a path to a yaml file that will contain all the options above.

### Insecure Certificates

You can set the env var `NODE_TLS_REJECT_UNAUTHORIZED=0` at the beginning of the start command when you're testing a system that uses https but has a self-signed or invalid SSL certificate. Just type this: `NODE_TLS_REJECT_UNAUTHORIZED=0 loadmill-agent start -t <INSERT_TOKEN_HERE>`&#x20;

IMPORTANT: The Loadmill agent won't be able to verify that it's talking to the right website in this case.

\
