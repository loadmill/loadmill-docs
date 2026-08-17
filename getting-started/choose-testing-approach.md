# Choose How You Want to Test

Loadmill supports several testing approaches. Choose the one closest to the behavior you want to validate. You can start with a single approach and combine them later.

| Approach | Best for | How tests are created | Where tests run |
| --- | --- | --- | --- |
| Droid mobile testing | Mobile user journeys and changing mobile interfaces | Plain-English instructions saved as reusable `.dcua` tests | Local devices, emulators, iOS simulators, cloud devices, CLI, and CI |
| API-first end-to-end testing | Business flows that cross APIs and services | Capture real application traffic or author API requests in the Test Editor | Loadmill-managed or private execution agents |
| Web UI and hybrid testing | Browser behavior, cross-browser coverage, and flows that combine API and UI validation | Playwright code, recorded browser actions, or UI Agent instructions | Desktop, private agents, and managed browser execution |
| Performance testing | Capacity, throughput, latency, and behavior under load | Create a load scenario or reuse an API flow | Loadmill's distributed load-testing infrastructure |

## Test a mobile app through the visible UI

Choose [Droid mobile testing](../droid-cua/README.md) when the mobile experience itself is what you need to validate. Droid acts through the screen instead of depending on selectors and coordinates.

## Validate a business flow at the API layer

Choose [API-first end-to-end testing](../api-testing/overview.md) when you want fast, deterministic coverage of the requests and services behind a real user journey.

For mobile applications, [Mobile API Testing](../introduction/deviceless-mobile-testing/README.md) captures the API traffic produced by the app. This is different from Droid: the capture happens on a device, but the generated test runs at the API layer.

## Validate browser behavior

Choose [web UI and hybrid testing](../hybrid-testing/overview.md) when the browser interface matters. Playwright steps validate exact browser interactions, while UI Agent steps handle goal-oriented tasks in natural language. Hybrid flows can use API steps for setup and Playwright for the UI behavior that must be observed.

## Validate capacity and reliability under load

Choose [performance testing](../load-testing/overview.md) when you need to understand how a system behaves under concurrent traffic or sustained demand.

## Combine approaches

A test strategy does not need to use only one approach. For example, a team can use API-first tests for fast regression coverage, Droid for critical mobile journeys, Playwright for browser-specific behavior, and performance tests before high-traffic events.
