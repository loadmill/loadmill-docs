# Droid CUA Agent Skill

The bundled Droid CUA Agent Skill gives supported coding agents the instructions they need to work safely with Droid CUA projects. It helps an agent inspect a `.dcua` project, author or update tests and context, check the selected target, and run or diagnose tests with the Droid CUA CLI.

Use the skill when you want an agent to work on a Droid CUA test project. It is intentionally limited to Droid CUA work; it is not a general browser automation or mobile-development skill.

***

## Install the skill

Install the latest Droid CUA package first:

```sh
npm install -g @loadmill/droid-cua
```

You can install the skill for Cursor, Claude Code, or Codex.

```sh
droid-cua skill install cursor
droid-cua skill install claude-code
droid-cua skill install codex
```

By default, the skill is installed globally for your user account. To install it only in the current project, add `--local`:

```sh
droid-cua skill install codex --local
```

In the Droid CUA desktop app, you can also choose **Help → Install Droid CUA Skill**, then select your coding agent. The desktop app installs the skill globally.

***

## Use the skill

After installation, ask your coding agent to work with Droid CUA or `@loadmill/droid-cua`. The skill directs the agent to:

* Inspect the active project without reading or exposing secret values.
* Work with existing `.dcua` tests, `context.md`, test data, and CLI configuration.
* Confirm the intended test and target before starting a run.
* Use Loadmill by default, unless you explicitly ask to use your own OpenAI API key.
* Run the narrowest relevant test and report its outcome, screenshots, and report artifacts.

For the CLI commands and supported test targets, see [CLI](cli.md).

***

## Manage an installation

Check whether a skill is installed:

```sh
droid-cua skill status codex
```

Remove an installed skill:

```sh
droid-cua skill uninstall codex
```

After upgrading `@loadmill/droid-cua`, explicitly update the installed skill:

```sh
droid-cua skill install codex --force
```

The installer does not overwrite or remove locally modified skill files unless you supply `--force`.
