# Loadmill Test Authoring Workflow

### 🚀 Overview

This guide explains how to create and update Loadmill test suites directly in your IDE (Cursor, VSCode, or any other editor) using the Loadmill MCP. With the MCP workflow you can:

* Create and update Loadmill tests directly from your IDE
* Validate changes instantly
* Run tests to ensure they work as expected
* Integrate new tests into your pipeline

> ⚠️ Before you get started, make sure you meet the [Prerequisites](test-authoring.md#prerequisites) below for this workflow.

### 🎥 Video Guide

Watch this demo to see how to create a new test suite using the Loadmill MCP:

{% file src="../.gitbook/assets/mcp-test-authoring.mp4" %}

### 📦 Where the Work Happens

All Loadmill suites live in a Git repository, and this repository is the **entry point** for creating and updating tests. By working directly in this repo:

* The actual changes happen alongside the suite files, just like any other code change.
* You are able to leverage GitHub MCP to pull context from anywhere in your system—PRs, API files, spec documents—but the resulting test updates remain local to the suite repo.
* The familiar Git workflow (branches → commits → PRs → review) applies naturally.

### 🧩 The `AGENTS.md` File

Each repository that contains Loadmill suites should include an `AGENTS.md` file that guides the IDE agent. This file defines:

* Where suites and flows live
* How the agent should structure and modify them
* When validation or execution should occur
* When to consult Loadmill Docs or GitHub MCP

`AGENTS.md` acts as a **baseline behavior model**, and you may extend it with project-specific conventions—for example:

* Naming standards
* Which Loadmill shared flows to use
* Common authentication patterns
* Internal testing best practices

With this file in place, the agent handles the workflow automatically. You only need to describe _what_ to build or change.

***

## 🔧 Main Workflows

There are two primary workflows when developing Loadmill tests in your IDE.

### Updating an Existing Test Suite

Use this process when adding flows or modifying existing test logic.

#### High-Level Steps

1. **Identify the suite to update**: Locate the relevant YAML file under `loadmill-suites/`.
2. **Apply the required changes**: Describe the new flow or modifications, the agent updates the YAML.
3. **Ensure the suite is valid**: The agent validates the suite and resolves any issues.
4. **Commit the changes to a branch**: A new Git branch is created, changes are committed, and the branch is pushed.
5. **Run the suite via MCP**: The suite is executed using that branch, and a link to the run is provided.
6. **Adjust if needed**: Update the suite and re-run until everything passes.
7. **Open a pull request**: Review and merge your changes.
8. _(Optional)_ **Sync the suite in Loadmill UI**: Use the GitHub Sync tab to check out the correct commit to view or edit it in the Loadmill UI.

**Important:** This last action will overwrite any unsynced changes in this suite in Loadmill, so be sure to sync first if needed.

### Creating a New Test Suite

Use this workflow when introducing a new suite for a feature or area.

#### High-Level Steps

1. **Create an empty suite**: The agent uses Loadmill MCP to generate a new suite in Loadmill.
2. **Create the actual test**: A new YAML file is created under `loadmill-suites/` with the generated content.
3. **Ensure the test is valid**: Validation is performed and issues are fixed.
4. **Commit to a new branch**: The suite is committed and pushed.
5. **Run the suite**: The agent executes it and provides a link to the run results.
6. **Adjust and re-run if necessary**: Continue until the suite passes.
7. **Open a pull request and merge**: Complete the standard Git workflow.
8. _(Optional)_ **Sync the suite in the Loadmill UI**: Checkout the commit using the GitHub Sync tab to view or edit it in the Loadmill UI.

### 🧭 Your Role as the Developer

The agent handles the lifecycle—validation, execution, branching, committing.\
You are responsible for:

* Describing the tests or updates you want
* Providing relevant context if needed (API changes, feature behavior, etc.)
* Reviewing the generated test logic
* Merging the resulting pull requests

The intent comes from you; the workflow is handled automatically.

### ✅ Summary

* Loadmill MCP enables you to build and update tests directly inside your IDE.
* Test logic lives in the repository and follows your normal development workflow.
* Loadmill MCP validates and executes tests; GitHub MCP manages branches and commits; Loadmill Docs MCP provides reference material.
* The `AGENTS.md` file defines your automation model and can be customized.
* Two main workflows are supported at the moment: updating an existing suite, or creating a new one.

**Note:** This functionality is currently in beta. Please provide feedback to help us improve it!

***

### 📘 Prerequisites

#### 1. Your Loadmill Suites Must Be Synced to Git

Your Loadmill test suites must be connected and synced to a Git repository. This enables version control, collaboration, and integration with the MCP workflow. For setup instructions, see: [Syncing Loadmill with GitHub](../integrations/github-integration/data-sync-connection-to-github.md)

#### 2. MCP Configuration

To use this workflow, you need to configure your MCP setup to include Loadmill and GitHub servers.

Example Cursor config:

```json
{
  "mcpServers": {
    "loadmill": {
      "command": "npx",
      "args": ["@loadmill/mcp"],
      "env": {
        "LOADMILL_API_TOKEN": "<YOUR_LOADMILL_API_TOKEN>"
      }
    },
    "loadmill-docs": {
      "url": "https://docs.loadmill.com/~gitbook/mcp",
    },
    "github": {
      "url": "https://api.githubcopilot.com/mcp/",
      "headers": {
        "Authorization": "Bearer <YOUR_GITHUB_TOKEN>"
      }
    }
  }
}
```

#### 3. `AGENTS.md` File

Your Loadmill tests repository should include an `AGENTS.md` file at the root level to guide the IDE agent. This file defines conventions, structure, and automation rules for your Loadmill suites and can be customized to fit your project's needs. Download the file and add it to your repository to get started:

{% file src="../.gitbook/assets/AGENTS.md" %}
