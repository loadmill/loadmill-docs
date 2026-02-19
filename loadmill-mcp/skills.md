# Loadmill Agent Skill

## Overview

Agent Skills are a new open standard for giving AI coding agents specialized capabilities. Tools like **Cursor**, **Claude Code**, **OpenAI Codex**, and **Goose** all support skills—portable instruction packages that agents discover and load automatically when a relevant task comes up.

The **Loadmill Agent Skill** gives your IDE agent everything it needs to create, maintain, and run Loadmill E2E tests as a natural part of your development workflow. Instead of context-switching to a separate testing tool, you describe what you need and the agent handles the rest—authoring YAML test files, validating them, running them via Loadmill MCP, and managing the Git workflow around them.

> **Prerequisite:** The Loadmill Agent Skill requires the **Loadmill MCP** server to be installed and configured in your IDE. See the [Installation guide](../loadmill-mcp/loadmill-mcp#installation) for setup instructions.

***

## Use Cases

### 1. Creating New Tests

Describe the scenario you want to test in plain text and the agent takes it from there. It creates a new Loadmill test suite, writes the flows, validates the YAML against the Loadmill schema, commits to a branch, runs the suite, and hands you a link to the results—all without leaving your IDE.

You can also point the agent at a **pull request for a new feature** and have it generate tests that cover the new behavior end-to-end. Or, direct it to a **buggy or uncovered section of your codebase** and let it create tests that fill the gap—turning blind spots into well-tested flows.

No prior Loadmill experience is needed; the skill encodes the structure, conventions, and best practices for you.

### 2. Test Maintenance

When your application code changes, tests need to change too. The Loadmill Agent Skill helps you keep your test suites in sync with your codebase. Point the agent at a PR, a diff, or simply describe what changed, and it will:

* Identify which test suites and flows are affected.
* Update assertions, request payloads, or flow logic to match the new behavior.
* Validate and re-run the updated tests to confirm everything passes.

This turns what used to be a manual, error-prone maintenance task into a quick conversation with your agent.

### 3. Running Regression Tests During Development

While building a new feature, you want continuous confidence that existing E2E flows still work—without waiting for CI. With the skill installed, you can ask your agent to run the relevant test suites or a full test plan against your **localhost** as you develop. The agent will:

* Execute the tests via Loadmill MCP against your local environment.
* Analyze failures and surface actionable insights.
* Help you fix any broken tests caused by intentional changes.
* Re-run until all regressions are resolved.

This creates a tight feedback loop—write code, run tests against your local server, fix issues—all inside your IDE, long before you push.

***

## Getting Started

### 1. Install Loadmill MCP

Follow the [Installation guide](https://docs.loadmill.com/loadmill-mcp/loadmill-mcp#installation) to configure the Loadmill MCP server in your IDE.

### 2. Download the Skill

Download the skill package below and extract it into your project's skills directory:

| IDE / Agent | Directory |
| --- | --- |
| Cursor | `.cursor/skills/loadmill` |
| Claude Code | `.claude/skills/loadmill` |
| OpenAI Codex | `.agents/skills/loadmill` |
| Goose | `.goose/skills/loadmill` |

{% file src="../.gitbook/assets/loadmill.zip" %}

### 3. Start Using It

Once the skill is in place, your agent will automatically pick it up. Try prompts like:

* _"Create an E2E test suite for the user registration flow"_
* _"Update the checkout tests to reflect the new payment API"_
* _"Run all regression tests for the billing module"_

The agent will follow the workflows defined in the skill—validating, committing, running, and reporting results—while keeping you in control at every step.
