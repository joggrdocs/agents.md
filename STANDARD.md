# The Standard

The `joggr/agents.md` standard is a simple standard for configuring a universal [`AGENTS.md`](https://github.com/openai/agents.md) that supports all of your codegen agents, and leverages your existing documentation to improve the quality of generated code.

## Goals

You have two primary goals that you should achieve to make sure your agents are well-equipped to generate code:

1. **Leverage your existing documentation** - Make sure your agents know about your existing documentation
2. **Link to your existing configs** - Link to your existing agent configuration file(s) to your `AGENTS.md` file

## Getting Started

### 1. Create a `AGENTS.md` file

If you don't already have one, create a `AGENTS.md` file in the root of your repository (if needed see [Monorepo Support](#monorepo-support)). 

### 2. Leverage your existing documentation

Once you have your initial `AGENTS.md` file, you need to make sure it leverages your existing documentation, for example:

```md
Always read the `CONTRIBUTING.md` file in the root of the repository, 
and follow the instructions, guidelines, and best practices.
```

or to help with testing:

```md
View the testing instructions in the `docs/testing.md` file in the root of the repository.
```

Just add whatever documentation you deem necessary, and your agents will automatically leverage it.

```md
# project-name

project-name is a project for doing something.

Always read the `CONTRIBUTING.md` file in the root of the repository, and follow 
the instructions, guidelines, and best practices.

## Structure

You can understand the repository structure by reading the `docs/structure.md` file in the root of the repository.

## Development Instructions

You can understand how to run the project by reading the `docs/development.md` file in the root of the repository.

## Testing Instructions

You can understand how to write & run tests by reading the `docs/testing.md` file in the root of the repository.
```

### 3. Add custom instructions (optional)

You may want to add custom instructions to your `AGENTS.md` file, for example:

```md
Always use vitest in all projects.
```

> [!TIP]
> You can view examples of other `AGENTS.md` files at the source [github.com/openai/agents.md](https://github.com/openai/agents.md)

### 4. Link to your existing configs

Depending on the agents you are using, you will need to point those agents to your `AGENTS.md` file.

For example, if you are using `claude-code`, you will need to copy the below block into your `CLAUDE.md` file:

```markdown
ALWAYS read the `AGENTS.md` in the root of the repository and apply the instructions to the current task.
```

And thats it! Your `claude` will now automatically read the `AGENTS.md` file in the root of the repository and apply the instructions to the current task.

> [!TIP]
> Certain agents like `cursor` required to add certain rules/logic (e.g. `globs`, `alwaysApply`) to the configuration file.

#### Pre-built examples

Below are a couple of pre-built examples to help you get started.

<details>
<summary>Claude Code - <code>CLAUDE.md</code></summary>

```markdown
ALWAYS read the `AGENTS.md` in the root of the repository and apply the instructions to the current task.
```

</details>


<details>
<summary>Cursor IDE - <code>.cursor/rules/agents.mdc</code></summary>

```yaml
---
description: Pointer to the `AGENTS.md` file in the root of the repository
globs: 
alwaysApply: true
---
Always read the `AGENTS.md` in the root of the repository and apply the instructions to the current task.
```

</details>

<details>
<summary>Windsurf IDE - <code>.windsurf/rules/agents.md</code></summary>

```yaml
---
trigger: always_on
---
Always read the `AGENTS.md` in the root of the repository and apply the instructions to the current task.
```
</details>

## Monorepo Support

If you are using a monorepo, you can create a `AGENTS.md` file in the root of your repository, and then create a `AGENTS.md` file in each of your packages.

You will need to update the configuration file(s) of your agents to point to the `AGENTS.md` file in the root of your repository, based on the agent you are using. 

For example, if you are using `windsurf`, you will need to update the configuration file(s) of your agents to point to the `AGENTS.md` file in the correct location, or leverage a simple prompt to find the `AGENTS.md` file in the correct location.

```markdown
- Always read the `AGENTS.md` file in the root of the repository, and apply the instructions to the current task
- Always read the `AGENTS.md` file closest to the working directory, and apply the instructions to the
  current task. If a `AGENTS.md` file is not found, walk up the directory tree until one is found, or 
  you reach the root of the repository.
```

You can also specifically point to the `AGENTS.md` file in the correct location using the agent's configuration file, for example:

`.windsurf/rules/agents-api.md`

```yaml
---
trigger: glob
globs: packages/api/**
---
Always read local `AGENTS.md` file, located at `<root>/packages/api/AGENTS.md`, and apply the instructions 
to the current task.
```