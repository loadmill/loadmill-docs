# Git-Based Playwright Workflows

Loadmill test suites can be synchronized with a Git repository so test changes are versioned, reviewed, and tied to the same delivery workflow as application changes. A suite containing Playwright steps is stored as Loadmill suite configuration, including its Playwright code.

## Connect a repository

Connect Loadmill to GitHub from **Settings → Integrations**, then select the repository used for test synchronization. Team administrator access is required to configure the connection.

See [GitHub Data Sync](../integrations/github-integration/data-sync-connection-to-github.md) for the complete setup.

## Review test changes in Git

Use the **GitHub Sync** tab in a test suite to choose a branch and commit the current suite configuration. Loadmill stores synchronized suites under `loadmill-suites/` in the selected repository.

From that point, test changes can follow a branch and pull-request workflow. Review the Playwright code and surrounding API steps together so the complete business flow remains understandable.

## Run a versioned test configuration

When running a Test Plan, select the branch under **Versioned Test Configuration**. Loadmill uses the committed suite configuration from that branch rather than uncommitted changes in the editor.

You can also use the [Loadmill MCP test authoring workflow](../loadmill-mcp/test-authoring.md) to update synchronized suites from a compatible AI development tool, validate the changes, and open them for review.

## Avoid overwriting unsynchronized work

Before checking out a branch or replacing the editor's working copy, make sure any changes that should be kept have already been synchronized. Checking out a committed suite version can replace unsynchronized editor changes.
