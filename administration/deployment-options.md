---
description: Compare Loadmill Cloud and Loadmill On-Prem and understand the infrastructure required for each deployment.
---

# Loadmill Deployment Options and Requirements

Loadmill is available as a managed cloud service or as a self-hosted on-prem deployment. Both options support Droid mobile testing alongside API, end-to-end, web, and performance testing. Droid tests can run interactively from the desktop application or automatically through CI/CD.

Choose a model based on where your applications are accessible, what data may leave your environment, which AI models you can use, and how much infrastructure your organization wants to operate.

## Deployment options at a glance

|  | Loadmill Cloud | Loadmill On-Prem |
| --- | --- | --- |
| **Loadmill Server** | Hosted and managed by Loadmill | Deployed inside the customer environment |
| **Test execution** | Loadmill cloud runners or customer-hosted runners | Customer-hosted runners inside the customer environment |
| **Droid execution** | Desktop application or CI/CD, connected to Loadmill Cloud | Desktop application or CI/CD, connected to the on-prem Loadmill Server |
| **AI model** | Models configured and managed by Loadmill | OpenAI models hosted by OpenAI or Azure, OpenAI open-weight models through AWS Bedrock, or supported self-deployed models such as Holo |
| **Database** | PostgreSQL and Redis managed by Loadmill | PostgreSQL and Redis deployed inside the customer environment |
| **Files and reports** | Managed cloud storage | Customer-managed local or S3-compatible storage |
| **Operations and upgrades** | Managed by Loadmill | Customer-operated infrastructure using Loadmill-provided Docker packages and upgrade guidance |

## Loadmill Cloud

Loadmill Cloud is the simplest option to adopt and operate. Loadmill manages the server, database, storage, AI models, availability, and platform upgrades.

Tests can run on Loadmill-managed cloud runners or from runners inside your environment. Droid always controls the target device from the desktop application or a CI/CD machine, while using Loadmill Cloud for authentication, AI models, orchestration, and reports.

### Private execution with Loadmill Cloud

Private execution is useful when the application under test is available only inside a corporate network or VPN. Install the Droid application or a Loadmill test runner inside that network and allow it to make outbound HTTPS connections to Loadmill Cloud. No inbound connection from Loadmill is required.

Requests between a private runner and the application under test remain inside the customer environment. Loadmill Cloud still manages the test definitions, orchestration, and results. For Droid, screenshots, context, prompts, and report artifacts may also be processed or stored in the cloud. Organizations with strict data-residency requirements should review these data flows before choosing this option.

### Network allowlisting

For Droid and customer-hosted runners, allow outbound HTTPS on TCP port 443 to `app.loadmill.com` and `pylon.loadmill.com`. Organizations that maintain a domain-level allowlist can allow `*.loadmill.com`. File and Droid report uploads may also require outbound HTTPS to the Loadmill-provided Amazon S3 endpoints.

The desktop application uses GitHub release services to download updates. These endpoints can be allowed separately, or the application can be distributed and updated through the organization's software-management process. If a corporate proxy or TLS inspection is in use, configure it for the desktop application and test runners.

No inbound firewall rule is required for private execution. If Loadmill cloud runners must reach an application inside the customer environment instead, make the target accessible through a gateway or allow connections from the current Loadmill runner IP addresses:

* `52.42.51.230`
* `54.190.108.53`
* `193.189.107.30`

Confirm the applicable region and production IP addresses with Loadmill before updating firewall rules.

## Loadmill On-Prem

Loadmill On-Prem is a self-hosted deployment for organizations that need to operate the Loadmill Server and its data within their own environment. Loadmill provides the platform as a convenient Docker-based deployment package, together with configuration and upgrade guidance.

The deployment connects the following components:

* **Loadmill Server:** Provides the web application, APIs, orchestration, and Droid AI gateway.
* **Database:** PostgreSQL stores persistent platform data, while Redis supports platform coordination and execution.
* **Files and reports:** Customer-managed storage holds uploaded files, attachments, and test reports. S3-compatible object storage is required when storing Droid report artifacts.
* **AI model:** The Loadmill Server connects to the selected hosted or self-deployed model.
* **Execution:** Droid desktop and CI/CD installations control mobile devices locally. Customer-hosted runners execute API, end-to-end, web, and performance tests.

### AI model options

An on-prem Loadmill Server can connect to OpenAI models hosted by OpenAI or Azure, as well as OpenAI open-weight models through AWS Bedrock. Loadmill also supports selected open-source models, including Holo, that can be deployed completely inside the customer environment.

The AI model must support the capabilities required by the selected Loadmill features. Droid requires a computer-use-capable model and a compatible endpoint. Loadmill will confirm the model, hosting option, credentials, and network path during deployment planning.

Using an on-prem Loadmill Server does not require the AI model itself to run on-prem. Organizations can use an approved hosted model, or keep the complete path private by deploying a supported model inside their environment.

### Infrastructure requirements

The exact capacity depends on concurrent Droid sessions, API executions, and load-test volume. A production design should cover:

* A supported container host for the Loadmill Docker deployment.
* PostgreSQL and Redis with persistent storage and backups.
* Local or S3-compatible object storage, with suitable retention and encryption policies.
* Network access between Loadmill, the AI model, test runners, Droid machines, and applications under test.
* Internal DNS and TLS certificates for the Loadmill Server.
* Windows or macOS machines for Droid, with access to the required physical devices, emulators, or simulators.
* Customer-hosted runners sized for the expected API, browser, and performance-testing capacity.
* Monitoring, secrets management, backup, recovery, and an agreed upgrade process.

Load testing capacity should be planned separately from the Loadmill Server. The number and size of execution agents depends on the required concurrency and request rate.

## Security and deployment review

Before selecting a deployment, agree on:

* Whether test definitions, results, screenshots, prompts, context, or reports may be processed outside the customer environment.
* Whether internal applications can be reached from cloud runners or require private execution.
* Which hosted or self-deployed AI models are permitted.
* Where database backups and report artifacts will be stored and how long they will be retained.
* Authentication and SSO requirements.
* Expected concurrent Droid, API, browser, and performance test runs.
* Network proxy, TLS inspection, firewall, and outbound-access requirements.
* Ownership of infrastructure monitoring, upgrades, and disaster recovery.

Once the model is selected, validate it with one Droid run and one representative API or end-to-end test. Confirm device access, runner connectivity, AI model access, result collection, report storage, and the required backup process before expanding the deployment.

## Related setup guides

* [Loadmill POC Setup](../poc-guides/Loadmill-POC-Setup.md) describes the minimum requirements for an initial evaluation.
* [Installation and Deployment Runbook](../poc-guides/Loadmill-Installation-Runbook.md) covers desktop, private, and cloud test runners.
* [On-Premises Setup](../poc-guides/loadmill-on-prem-setup.md) provides the Docker-based installation steps.
* [Droid Mobile Testing Quickstart](../droid-cua/getting-started.md) covers the Droid desktop and first-test setup.
