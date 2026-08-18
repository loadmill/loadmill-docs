# Table of contents

## Get Started

* [Loadmill Overview](README.md)
* [Choose How You Want to Test](getting-started/choose-testing-approach.md)
* [Create Account](quick-guide/create-account.md)
* [Droid Mobile Testing Quickstart](droid-cua/getting-started.md)
* [API-First E2E Quickstart](quick-guide/quick-start-guide.md)
* [Web UI and Playwright Quickstart](hybrid-testing/quickstart.md)
* [Performance Testing Quickstart](load-testing/getting-started-1.md)

## Droid Mobile Testing

* [Droid Mobile Testing Overview](droid-cua/README.md)
* [Setup](droid-cua/setup.md)
  * [Setup Troubleshooting](droid-cua/setup-troubleshooting.md)
* [Best Practices](droid-cua/best-practices.md)
* [Common Testing Mistakes](droid-cua/common-mistakes.md)
* [Testing Web Applications with Droid](droid-cua/web-testing.md)
* [Reviewing Droid Runs in Loadmill](droid-cua/runs-dashboard.md)
* [CLI](droid-cua/cli.md)
* [Running Droid Tests in CI](droid-cua/ci.md)
* [Agent Skill](droid-cua/skill.md)

## API-First End-to-End Testing

* [Overview](api-testing/overview.md)
* [Register Your First API Flow](quick-guide/register-your-first-api-flow.md)
* [Running Your API Test](quick-guide/running-your-api-test.md)
* [Capture API Traffic](user-behavior-testing/working-with-the-recorder.md)
  * [Download Test Composer](quick-guide/download-test-composer.md)
  * [Test Composer Setup](loadmill-test-composer/quickstart.md)
  * [Test Composer Layout](loadmill-test-composer/composer-layout.md)
  * [Filter Settings](loadmill-test-composer/filter-settings.md)
  * [Algorithm Configuration](loadmill-test-composer/algorithm-settings.md)
  * [Mobile API Testing](introduction/deviceless-mobile-testing/README.md)
    * [Capturing Mobile API Traffic](introduction/deviceless-mobile-testing/capturing-traffic-with-loadmill-mitm-proxy.md)
    * [Installing the Loadmill Desktop App](introduction/deviceless-mobile-testing/installing-loadmill-desktop-app/README.md)
      * [Install Windows Desktop App](introduction/deviceless-mobile-testing/installing-loadmill-desktop-app/install-windows-desktop-app.md)
    * [Loadmill Desktop Recorder](introduction/deviceless-mobile-testing/loadmill-desktop-recorder/README.md)
      * [Generating API Test Flows](introduction/deviceless-mobile-testing/loadmill-desktop-recorder/generating-test-flows.md)
    * [Installing Certificates on Mobile Devices](introduction/deviceless-mobile-testing/installing-certificate-on-mobile-devices/README.md)
      * [iOS Certificate Installation](introduction/deviceless-mobile-testing/installing-certificate-on-mobile-devices/ios-certificate-installation.md)
      * [Android Certificate Installation](introduction/deviceless-mobile-testing/installing-certificate-on-mobile-devices/android-certificate-installation.md)
    * [Configuring the Mobile Proxy](introduction/deviceless-mobile-testing/configuring-proxy-on-mobile-devices/README.md)
      * [iOS Wi-Fi Settings](introduction/deviceless-mobile-testing/configuring-proxy-on-mobile-devices/ios-wi-fi-settings.md)
      * [Android Wi-Fi Settings](introduction/deviceless-mobile-testing/configuring-proxy-on-mobile-devices/android-wi-fi-settings.md)
    * [Mobile Capture Troubleshooting](introduction/deviceless-mobile-testing/troubleshooting.md)
  * [Additional Capture Methods](user-behavior-testing/additional-recording-methods.md)
    * [Set Up Application Recording](user-behavior-testing/setting-up-the-recorder.md)
    * [Embed the Recording Service Worker](working-with-the-recorder/embedding-the-recording-service-worker.md)
  * [Recorder Settings](user-behavior-testing/recorder-settings.md)
  * [Recording Troubleshooting](user-behavior-testing/recording-troubleshooting.md)
  * [How to Work with Recordings](user-behavior-testing/working-with-the-recorder-1.md)
* [Contract Testing](introduction/api-server-testing/contract-testing.md)
* [Regression Testing](introduction/api-server-testing/regression-testing.md)
* [Testing with CORS](auth/testing-with-cors.md)
* [API Testing FAQs](general/api-testing1/api-testing-faqs.md)
* [API Testing Troubleshooting](general/api-testing1/api-testing-troubleshooting.md)

## Web UI and Hybrid Testing

* [Overview](hybrid-testing/overview.md)
* [Playwright Integration Capabilities](hybrid-testing/capabilities.md)
* [Agent Testing Quickstart](quick-guide/agent-testing-quick-guide.md)
* [Hybrid API and UI Tutorial](hybrid-testing/hybrid-api-ui-tutorial.md)
* [Cloud and Cross-Browser Execution](hybrid-testing/cloud-cross-browser-execution.md)
* [Git-Based Playwright Workflows](hybrid-testing/git-based-playwright-workflows.md)
* [Debugging Playwright Tests](hybrid-testing/debugging-playwright-tests.md)

## Performance Testing

* [Overview](load-testing/overview.md)
* [Configure a Load Test](load-testing/working-with-the-test-editor.md)
* [Analyzing Performance Test Results](load-testing/analyzing-load-test-results.md)
* [Parameterized Load Tests](load-testing/creating-a-parameterized-load-test.md)
* [Domain Verification](load-testing/domain-verification.md)
* [Configuration Files](load-testing/configuration-files.md)
* [Performance Testing FAQs](load-testing/load-testing-faqs-1.md)
* [Performance Testing Troubleshooting](load-testing/load-testing-faqs.md)
  * [Common Load Test Issues](load-testing/load-tests-issues.md)

## Test Editor Reference

* [Layout](test-editor/layout.md)
* [Flows](test-editor/flows/README.md)
  * [Generated Flow Code](test-editor/flows/generated-flow-code.md)
  * [Test Flow Editor](test-editor/flows/test-flow-editor.md)
  * [Flow Controls](test-editor/flows/flow-controls.md)
  * [Groups](test-editor/flows/groups.md)
  * [Add CSV to Flow](test-editor/flows/add-csv-to-flow.md)
  * [Flow Execution](test-editor/flows/flow-execution.md)
* [Steps](test-editor/steps/README.md)
  * [Request Step](test-editor/steps/request-editor.md)
  * [Code Step](test-editor/steps/code-step.md)
  * [Extraction and Assertion Step](test-editor/steps/extraction-and-assertion-step.md)
  * [WebSocket Step](test-editor/steps/web-socket-step.md)
  * [Playwright Step](test-editor/steps/playwright-step.md)
  * [UI Agent Step](test-editor/steps/ui-agent-step.md)
* [Extractions](general/api-testing1/test-suite-editor/set-parameters-extractions.md)
* [Assertions](general/api-testing1/test-suite-editor/assertions.md)
* [Parameters](general/api-testing1/test-suite-editor/parameters/README.md)
  * [Parameter Execution Order](general/api-testing1/test-suite-editor/parameters/parameter-execution-order.md)
  * [Test Suite Parameters](general/api-testing1/test-suite-editor/test-suite-parameters.md)
  * [Suite Execution Mode](general/api-testing1/test-suite-editor/suite-execution-mode.md)
  * [Parameter Sets](test-editor/parameters/parameters-sets.md)
* [Built-in Functions](general/api-testing1/test-suite-editor/functions.md)
* [Postscript](test-editor/postscript/README.md)
  * [Running Postscript](test-editor/postscript/running-postscript.md)
  * [Accessing with Postscript](test-editor/postscript/accessing-w-postscript.md)
  * [Validating Postscript](test-editor/postscript/validating-postscript.md)
  * [Using Built-in Functions in Postscript](test-editor/postscript/built-in-functions.md)
* [Authentication Flows](general/api-testing1/test-suite-editor/global-login-flow.md)
* [Before and After Hooks](general/api-testing1/test-suite-editor/before-and-after-hooks.md)

## AI and Developer Workflows

* [Loadmill MCP Overview](loadmill-mcp/loadmill-mcp.md)
* [Test Authoring Workflow](loadmill-mcp/test-authoring.md)
* [Loadmill Agent Skill](loadmill-mcp/skills.md)

## Specialized Testing

* [Database Testing](general/api-testing1/db-testing-using-queries.md)
* [Email Testing](general/api-testing1/testing-emails.md)
* [Kafka Testing](integrations/kafka-testing.md)
* [Webhook Testing](integrations/webhook-testing.md)
* [gRPC Support](integrations/grpc-support.md)
* [Mocking](integrations/mocking.md)

## Integrations and CI/CD

* [Loadmill Agent](general/api-testing1/testing-localhost-application.md)
* [CI Integration](integrations/npm-modal.md)
* [GitHub](integrations/github-integration/README.md)
  * [GitHub CI Integration](integrations/github-integration/ci-integration.md)
  * [GitHub Data Sync](integrations/github-integration/data-sync-connection-to-github.md)
* [GitLab](integrations/gitlab.md)
* [Bitbucket](integrations/bitbucket.md)
* [Jira](integrations/jira.md)
* [TestRail](integrations/testrail.md)
* [Slack](integrations/slack-integration.md)
* [Datadog](integrations/datadog-integration.md)
* [New Relic](integrations/new-relic.md)
* [XRay](integrations/xray.md)
* [Integrations FAQs](integrations/integrations-faqs-1.md)

## Results and Teamwork

* [Running a Test Suite](general/api-testing1/analyzing-an-api-test-results.md)
* [Test Plans](general/api-testing1/test-plan.md)
* [API Catalog and Coverage](reporting/api-catalog-and-coverage/README.md)
  * [API Catalog](reporting/api-catalog-and-coverage/api-catalog/README.md)
    * [Unique Entity ID Mapping](reporting/api-catalog-and-coverage/api-catalog/unique-entity-ids-mapping.md)
    * [Domain Mapping and Grouping](reporting/api-catalog-and-coverage/api-catalog/domain-mapping-and-grouping.md)
    * [Endpoint Grouping](reporting/api-catalog-and-coverage/api-catalog/endpoints-grouping.md)
    * [OpenAPI Upload](reporting/api-catalog-and-coverage/api-catalog/openapi-upload.md)
  * [Test Coverage](reporting/api-catalog-and-coverage/test-coverage/README.md)
    * [Generating an API Test Coverage Report](reporting/api-catalog-and-coverage/test-coverage/generating-api-test-coverage-report.md)
* [Collaboration Overview](collaboration/collaboration.md)
* [Teams](collaboration/teams.md)
* [Groups and Reports](collaboration/groups-and-reports.md)
* [Test Suite Collaboration](collaboration/test-suite-collaborators-1.md)
* [Reviews](collaboration/reviews.md)
* [Shared Flows](collaboration/shared-flows.md)
* [Labels](collaboration/labels-and-filters.md)

## Administration and Deployment

* [Settings](general/account-settings/README.md)
  * [Analytics](general/account-settings/analytics/README.md)
    * [Flow Run History](general/account-settings/analytics/flow-run-history.md)
  * [Import and Export](general/account-settings/import-and-export.md)
* [Billing](general/billing/README.md)
  * [Usage Report](general/billing/usage-report.md)
* [API Tokens](auth/api-tokens.md)
* [Okta SSO Integration](auth/okta-sso-integration.md)

## POC Guides

* [Loadmill POC Setup](poc-guides/Loadmill-POC-Setup.md)
* [Installation and Deployment Runbook](poc-guides/Loadmill-Installation-Runbook.md)
* [On-Premises Setup](poc-guides/loadmill-on-prem-setup.md)

## Help and Reference

* [General FAQs](general/faq.md)
* [General Troubleshooting](general/general-troubleshooting.md)
* [REST API](auth/rest-api.md)
* [Migration Guide](general/migration-guide.md)
* [Glossary](GLOSSARY.md)
* [Comparisons](general/comparisons/README.md)
  * [Loadmill vs. SoapUI](general/comparisons/loadmill-vs.-soapui.md)
  * [Loadmill vs. JMeter](general/comparisons/loadmill-vs.-jmeter.md)
  * [Loadmill vs. Blazemeter](general/comparisons/loadmill-vs.-blazemeter.md)
  * [Loadmill vs. WebdriverIO](general/comparisons/loadmill-vs.-webdriverio.md)
  * [Loadmill vs. Potato](general/comparisons/loadmill-vs.-potato.md)
