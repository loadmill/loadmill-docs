# Common Droid Testing Mistakes

Droid tests are most effective when they validate a focused user journey through the visible product. Many unreliable tests begin by asking Droid to do work that belongs in a different test, a shared project file, or another testing layer.

Use this page as a quick review when a test is slow, difficult to understand, or inconsistent between runs. For the reasoning behind these recommendations, see [Writing Reliable Droid CUA Tests](best-practices.md).

***

## Putting the whole journey in one instruction

An instruction such as _buy a product, apply a coupon, change the delivery address, pay, and verify the order_ gives the agent too many intermediate decisions without useful checkpoints.

Break the journey into short-term goals and verify the important state changes:

```text
Search for "Amul Toned Milk 1L" and add it to the cart.
Verify that the cart badge shows "1".
Open the cart and continue to checkout.
Apply the coupon "WELCOME10".
Verify that the discount appears in the order summary.
Complete checkout and verify that the confirmation screen is visible.
```

One instruction does not need to equal one tap. It should express one meaningful piece of the journey that the agent can complete and evaluate before moving on.

***

## Putting every business path in one test

A long test that signs in, edits a profile, searches, checks out, changes settings, and signs out is difficult to diagnose and expensive to repeat. Split unrelated behaviors into independently runnable tests.

Keep dependent actions together when they form one business journey. A maker creating a transaction and a checker approving that same transaction may belong in one test because the second part depends on the first. Separate files should not depend on running in a particular order.

***

## Testing backend permutations through the UI

Before adding many variations, ask what you are trying to prove.

Use Droid when the visible client behavior matters: the user can complete checkout, the correct validation appears, or a role sees the correct controls. Use a Droid Scenario Run when a small set of meaningful user-facing conditions should exercise the same journey.

Use Loadmill API testing when the real goal is to validate a business rule across dozens or hundreds of inputs. Repeating the same frontend journey for every country, price, permission combination, or response shape is slower and provides little additional UI evidence.

| What needs validation | Best starting point |
| --- | --- |
| A user can complete a visible mobile or web journey | Droid |
| The same journey under a few meaningful user conditions | Droid Scenario Run |
| Many data combinations or backend rules | Loadmill API testing |
| Data or account state needed before a UI journey | A Loadmill API flow followed by Droid |

The strongest test may combine the layers: prepare exact state through an API flow, then let Droid validate what the user experiences.

***

## Creating all setup through the interface

Driving through unrelated screens to create policies, accounts, transactions, or catalog data makes the test longer without improving coverage of the behavior under test.

When setup is not part of the scenario, create it with an existing Loadmill flow and continue through the UI with the returned state. Use the interface for setup only when that setup experience is itself what the test needs to validate.

***

## Rewriting natural language as a brittle script

Detailed instructions such as _tap the third icon, click the first card, then press the button below the price_ depend on the current layout and hide the purpose of the test.

Prefer a short-term goal such as _search for the product and add the 1L package to the cart_. Add an exact label or interaction only when it disambiguates the route or when that interaction is part of the behavior being tested.

***

## Using vague assertions

_Verify it worked_ does not define what success looks like. Name the stable, visible evidence:

* Verify that the order status is **Confirmed**.
* Verify that the cart badge shows **1**.
* Verify that the **Select address** screen is visible.

Prefer durable results over animations, loading states, and short-lived toast messages.

***

## Turning `context.md` into another test script

Project context is shared product knowledge, not a hidden list of steps for one scenario. Do not copy the current test into `context.md`, add one-off test values, or document temporary workarounds just to make a failing run pass.

Keep journey-specific instructions in the `.dcua` test, reusable non-secret variation data in `test-data.md`, and credentials in `.secrets`. Add something to `context.md` when another test or a new teammate would benefit from knowing it too.

***

## Rerunning without learning from the failure

An unchanged rerun is reasonable for a clearly temporary device, provider, or network problem. Repeated retries are not a substitute for diagnosing an ambiguous instruction, stale context, unavailable target, or product regression.

Find the first meaningful divergence, classify it, and change the smallest evidence-supported input. Do not weaken an assertion or document broken product behavior as context merely to produce a passing result.

***

## Treating one pass as proof of readiness

A passing run may still contain repeated typing, reopening screens, resubmitting actions, or unexplained recovery. Review the report and make sure the path was direct enough to trust in routine execution.

Start a new test with Loadmill Smart. Once the journey is stable and its evidence is clean, compare it with Loadmill Pulse for faster routine runs.

***

## A quick review before saving

Before calling a test ready, check that:

* Each instruction expresses a clear short-term goal.
* Assertions name visible evidence.
* The test covers one coherent, independently runnable journey.
* Backend setup and large data matrices are not being forced through the UI.
* Shared product knowledge, run data, and secrets are stored in the right files.
* A representative run completed without unexplained recovery.
