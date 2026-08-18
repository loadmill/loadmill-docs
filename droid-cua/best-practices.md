# Writing Reliable Droid CUA Tests

If you are arriving from Playwright, Appium, Selenium, or another locator-based automation framework, the most important thing to understand is that Droid CUA is not a faster way to write the same kind of test. It is a different layer of automation.

Traditional frameworks run scripts against implementation-level targets such as selectors, element IDs, and DOM structures. Droid CUA gives a computer-using agent a goal, a screen, and product-specific guidance, then lets it operate the product the way a person would. That shift changes what a test is, how you write one, and what makes it reliable.

This guide focuses on that craft. Installation, target setup, and command-line options are covered separately in [Setup](setup.md) and [CLI](cli.md).

***

## Brief a teammate, not a robot

The most useful mental model for Droid CUA is that you are handing a task to a smart new teammate. They can read your instruction, see the current screen, and use the knowledge supplied by the project. They do not automatically know your product, environment conventions, account roles, or team shorthand.

If that teammate would reasonably ask a follow-up question before acting, the instruction is not ready yet.

This model tells you when an instruction is too vague, when it is too detailed, what belongs in the test, what belongs in project context, and why assertions must describe something the agent can actually observe.

### Find the useful middle

There are roughly three levels at which you can write a Droid instruction.

At the highest level is the complete goal: _buy a product and verify the order is confirmed_. At the lowest level are exact interactions: tap this field, type this value, open this menu, tap this button. Between them are short-term goals: _search for the product_, _add it to the cart_, _complete checkout_, _verify the confirmation_.

Most reliable tests live in that middle layer.

A complete goal gives the agent a great deal of freedom. That can be useful in Design Mode or exploratory work, but repeatable execution may force the agent to rediscover the route every time or let it choose a path you did not intend to test. Exact interaction instructions have the opposite problem: they couple the test to incidental details of the current layout and turn natural language into a brittle script.

Short-term goals preserve intent while giving the journey enough shape to stay focused and repeatable. Move higher when the route truly does not matter. Move lower when the screen is ambiguous, when an intermediate state is part of the behavior under test, or when run evidence shows that the agent needs more help. You are not choosing one level for the whole test; you are giving each part of the journey the amount of guidance it needs.

### Precision still matters

Natural language is the interface, but precision is still the discipline. Instead of precise selectors, you need an unambiguous goal, the right product language, and an observable result.

Use an exact control label when it distinguishes one action from another, but do not prescribe every visible control when a short-term goal is already clear. _Check that checkout works_ is not precise. _Complete checkout and verify the Select address screen is visible_ is.

Too high-level: _Order something from the store._

Balanced: _Search for "milk", add "Amul Toned Milk 1L" to the cart, and verify it appears in the cart._

Too detailed: _Tap the search field, type milk, press Enter, tap the first card, and tap the button below the price._

The detailed form is justified only when those interactions are important or the balanced instruction has proved unreliable.

***

## Understand what the agent sees

The agent experiences the interface as a sequence of screenshots rather than continuous motion. At each turn it receives the current screen, the current instruction, relevant project knowledge, and the working history Droid maintains for the run. It chooses an action, Droid executes it, and a new screenshot comes back.

This explains why the agent may take another screenshot to confirm a state change, why something remembered from earlier may no longer be actionable, and why it must find a control again after it scrolls out of view.

Animations, short-lived toast messages, loading transitions, and temporary empty states can happen between screenshots. Prefer assertions about the durable state that follows them. An explicit wait can be appropriate when the product genuinely needs time, but it should explain a known transition rather than hide an unexplained failure.

### Visible state is evidence

The agent works through the interactions available on the current target: taps or clicks, typing, scrolling, key presses, and waits. A visible state change is evidence that a mutating action such as submit, create, approve, reject, login, logout, or send succeeded.

If the only immediate confirmation that a form was submitted is that its fields clear and the button returns to its idle state, describe that stable product behavior in context. Then add an assertion for the business result the test actually cares about.

Repeated actions are worth noticing even when the run eventually passes. Reopening a screen, typing the same value again, or resubmitting a form may be harmless recovery, but it may also reveal an ambiguous instruction, unstable product behavior, or a bug the agent managed to work around. A pass tells you where to begin reviewing the evidence; it does not make that evidence irrelevant.

### Assertions are the verification contract

An assertion is its own instruction where the agent's job changes from acting to verifying. It examines the screen, decides whether the expected result is visible, and returns a clear pass or fail verdict.

You can write an explicit `assert:` line or simply say _verify that..._ in natural language. Strong assertions name a badge, label, screen title, status, value, or message. _Verify it worked_ is weak. _Verify the cart badge shows "1"_ names an observable result.

Add assertions after important state changes, at the end of a business flow, at meaningful checkpoints in a longer journey, and after expected error paths.

***

## Give project knowledge a clear home

A useful Droid project separates the journey, the team's shared knowledge, the data for a run, and sensitive values instead of forcing all of them into one file.

Think of the `.dcua` test as the assignment you hand to a teammate. `context.md` is the product handbook they already know. `test-data.md` is a run sheet containing non-secret people, products, roles, and scenario combinations. `.secrets` is the locked envelope containing credentials or other sensitive values. `.env` contains the infrastructure credentials Droid itself needs. A checked-in Droid config records the shared execution settings that make headless runs reproducible.

Each non-empty line in a `.dcua` file is one instruction or assertion, and `//` starts a comment for human readers. One instruction is not the same as one tap. Keep the journey readable from top to bottom, state the starting condition when the environment does not guarantee it, and keep secret values out of the file.

Use the names of keys from `.secrets`, such as `USER_EMAIL` and `USER_PASSWORD`, so the agent can request those values without placing them in its prompt or the run log. Keep both `.secrets` and `.env` out of version control.

A project should normally have one shared context file and one shared Droid config. Reuse them across the project's tests instead of creating a special context or config for every scenario.

### Write context for a new teammate

`context.md` should answer one question: _what would a capable new teammate need to know before testing this product for the first time?_

Start with an overview of the product, its main screens, and its top-level navigation. Explain the roles and what each one can do without including passwords or other secrets. Add non-obvious navigation, environment banners, product terms that are easy to confuse, and recurring success signals that help the agent recognize what happened.

Visual cues deserve their own line. If new items appear at the bottom of a separately scrolling list, say so. If a list refreshes in place rather than opening a new screen, say so. If two controls look nearly identical, explain how to tell them apart.

Context is not a copy of the test. Avoid scenario-specific steps, values that belong in `test-data.md`, UI text the agent can already see, speculative workarounds, and stale information. A context file that silently lies about the product is worse than no context file at all.

### Build context alongside the test

You do not need to describe the entire application before writing the first test. Start with a focused journey, create the test and `context.md` together, and add knowledge when the work reveals that the agent needs it.

When you encounter a missing detail, decide where it belongs:

* If it is part of only this journey, add it to the `.dcua` test.
* If it is stable product knowledge that other tests or a new teammate would reuse, add it to `context.md`.
* If it changes between runs, add it to `test-data.md`.
* If it is sensitive, add it to `.secrets` and refer to the secret by name.

For example, the test can say _create a transfer as maker and approve it as checker_. The context can explain what the maker and checker roles mean, where pending transfers appear, and that an approved transfer disappears from the pending list. Those facts are useful beyond one scenario; the exact transfer journey is not.

After a failure, add context only when the missing knowledge is true, stable, and reusable. Do not encode a product bug, temporary state, or one-off workaround as if it were normal application behavior. This iterative approach keeps context useful without turning it into another test script.

***

## Design once, then make the journey repeatable

Design Mode turns a testing idea into a draft test. Bind the session to the relevant project so the agent can use its context during exploration, then describe the business goal rather than prescribing the route.

_Create a transfer as maker, approve it as checker, and verify the approved transaction disappears from the pending list_ is a useful Design Mode prompt. A detailed tap-by-tap script is not; the point of Design Mode is to discover the route for you.

The generated `.dcua` file is a first draft. Review whether it uses short-term goals, remove accidental exploration, clarify ambiguous transitions, and strengthen the assertions before treating it as ready. Design Mode accelerates the craft of writing a test; it does not replace it.

### Close the loop with Jira

A Jira ticket can be the starting point for a Design Mode session, but it is rarely an executable test as written. Tickets often omit the account and environment assumptions, concrete data, visible labels, and explicit success criteria the agent needs. Treat the generated journey as a draft that still requires the same review as any other test.

The loop also works in the other direction. After a failed run, Droid can prepare a Jira ticket containing the failing instruction, recent execution context, target details, and a summary of what went wrong. Review that draft before filing it. The goal is to preserve useful evidence and save typing, not to turn every failed run into an automatic bug report.

### Prepare state through APIs

Many end-to-end tests need data that is slow or awkward to create through the interface. An insurance claim may require an active policy. An approval test may need a pending transaction. Driving through unrelated screens to create that state makes the test longer and less reliable without adding useful coverage.

A `.dcua` test can invoke an existing Loadmill flow before continuing through the UI. Write `loadmill:` followed by a distinctive description of the saved flow, or use a natural instruction such as _Run the Loadmill create premium customer flow with country=US._ Droid finds the best matching flow, waits for it to finish, and makes relevant returned information available to later instructions.

Refer to that information by meaning, as in _sign in as the customer created by the Loadmill flow_, rather than inventing placeholder syntax. Use an API flow to establish the state the scenario needs, then use Droid to verify the behavior the user experiences.

### Run one journey under different conditions

Data-driven testing in Droid does not require turning a readable journey into a parameterized program. A normal run executes the `.dcua` test once, exactly as written. A Scenario Run combines the unchanged test with a plain-language request such as _run checkout with each buyer account and each in-stock product_.

Reusable, non-secret accounts, products, roles, regions, and scenario combinations can live in `test-data.md`. Droid previews the cases it plans to run so you can check that it understood the request and notice an unexpectedly large fan-out. Each case receives only the relevant data for that run.

The generated cases are execution results, not new test files, and the original journey stays free of `{email}` or `{{product}}` placeholders. Use a normal run when you want one known journey. Use a Scenario Run when the variation is the point of the exercise.

***

## Start with Smart, then earn the switch to Pulse

Begin with Loadmill Smart while you are designing and stabilizing a new test. Smart gives a new or difficult journey the strongest starting point.

Once the test is clear, repeatable, and no longer relying on recovery, compare the same journey with Loadmill Pulse. Pulse is faster and more efficient for routine execution. Keep the change only if the test remains stable on the same target and application state.

Changing models is a comparison, not a cure for an ambiguous instruction, stale context, target problem, or product regression. Beacon is experimental and is better treated as an intentional evaluation.

***

## Know the local web boundary

Droid can connect to a locally installed Chrome or Edge browser. The same instruction-writing principles apply, but the agent operates inside the web page frame.

It can interact with the site and navigate as part of the test. It cannot use the browser's address bar, settings, bookmarks, extensions, or other browser chrome. Write web tests as journeys through the application, not as instructions for operating the browser itself.

For setup and execution commands, see [Setup](setup.md#web-setup) and [CLI](cli.md#run-a-saved-web-test).

For a complete local and cloud browser workflow, see [Testing Web Applications with Droid](web-testing.md).

***

## Keep tests focused and independent

Short tests are easier to understand and maintain, but splitting is safe only when every resulting test can run independently.

Separate unrelated flows such as signing in, editing a profile, and checking out when each has its own setup and observable result. Keep a maker-create/checker-approve journey together when the second half depends on state created by the first. Droid does not guarantee that separate test files will run consecutively or share state, so ordered files are not a substitute for one independently runnable scenario.

If setup dominates the behavior under test, consider preparing that state through a Loadmill flow rather than breaking one dependent journey into several files.

***

## Classify a failure before editing the test

Find the first place where the run diverged from your intent. Everything after it is usually downstream.

A missing credential or dependency is setup. An unavailable device or browser is a target problem. Multiple reasonable interpretations point to the test or stale project knowledge. A temporary provider or network problem may justify one unchanged rerun. A crash, product error, or consistent violation of a clear assertion is an application regression and should stop the healing loop.

Do not turn broken product behavior into new context, add a broad wait to cover it, or weaken the assertion until it passes.

Fix the smallest evidence-supported set of inputs. If the agent selected the wrong account because two similar accounts were visible, the instruction, context, or test data may need to disambiguate them. If it completed the action but the test did not prove the result, strengthen the assertion. Rewriting the entire journey should be the last thing you try.

### A pass is a baseline, not automatic readiness

Review whether the agent repeated actions, reopened screens, recovered from losing state, or took far longer than expected. Those behaviors may not change the final verdict, but they affect whether the test is trustworthy in CI.

A straightforward journey may need only one clean representative pass after refinement. A flaky, state-sensitive, or materially changed test deserves another unchanged run. Call it ready when its assertions pass, its important behavior is still covered, and no unexplained recovery loop remains.

***

## Treat the evidence as part of the test

A run produces more than a green or red result. Screenshots show what the agent could see at important moments. The HTML report reconstructs the instruction and action timeline in a form you can share. A replay video makes the journey easy to review when motion or timing matters. Explain Mode provides short explanations for non-obvious decisions, while debug artifacts provide a deeper record for diagnosis.

Use the lightest artifact that answers the question. The report is the normal handoff. Screenshots are the fastest way to locate a visible divergence. Video helps when timing between frames matters. Device, Appium, or browser logs help separate product behavior from platform or automation behavior.

Artifacts should support the conclusion, not force another person to discover it for themselves.

### Working through a coding agent

The [Droid CUA Agent Skill](skill.md) lets coding agents such as Codex, Cursor, and Claude Code inspect a project, author or improve a `.dcua` test, run it through the CLI, and return the evidence in the same conversation where development work is happening.

Brief the coding agent on the behavior you want checked. It should inspect the existing project conventions, propose the test and target, and ask for confirmation before starting a run. During execution it can show safe progress screenshots. Afterward it should give you the result, the first meaningful problem it found, what changed during any improvement loop, and a link to the final report.

For a new, flaky, or slow test, ask the coding agent to stabilize or optimize it rather than merely make it pass once. That authorizes a baseline followed by evidence-driven edits and representative reruns on the same target. It does not authorize changing application code, weakening assertions, or silently switching providers or models.

***

## What this enables

Teams that adopt these practices stop writing scripts and start briefing a teammate. They use short-term goals to give a journey shape without coupling it to every interaction. They keep product knowledge, test data, and secrets in the right places. They use Design Mode to discover a route, API flows to prepare state, Scenario Runs to vary conditions, and coding agents to bring the workflow into development.

Most importantly, they treat reports and recovery behavior as evidence rather than stopping at a green verdict. Reliability comes from the quality of the brief, the clarity of its assertions, and the discipline to examine what actually happened.

When you are ready to put these practices into use, continue with the [Droid Mobile Testing Quickstart](getting-started.md), review the [Common Droid Testing Mistakes](common-mistakes.md), or move on to [Setup](setup.md) and the [CLI reference](cli.md).
