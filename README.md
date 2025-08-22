# `joggr/agents.md`

A standard for configuring a universal [`AGENTS.md`](https://github.com/openai/agents.md) that supports all of your codegen agents, and leverages your existing documentation to improve the quality of generated code.

## Why?

### `AGENTS.md` is not supported by all agents

Not all agents will automatically look for a `AGENTS.md` file in the root of the repository, for example tools like `cursor`, `claude`, etc. have their own configuration files.

### Great documentation improves the quality of generated code

At Joggr, we have been working with our customers to automatically generate a `AGENTS.md` and keep it up-to-date, in addition to their standard `markdown` documentation. We've seen significant improvements in the quality of generated code when a repository has great documentation, but you also need to make sure your agents KNOW about those great docs.

## Who?

Below are some examples of repositories using the `joggr/agents.md` standard:

- [viteval](https://github.com/viteval/viteval) - A framework for evaluating LLMs using TypeScript powered by Vitest

## The Standard

To use the `joggr/agents.md` standard, you will need a `AGENTS.md` file in the root of your repository. You have two primary goals that you should achieve to make sure your agents are well-equipped to generate code:

1. **Leverage your existing documentation** - Make sure your agents know about your existing documentation
2. **Link to your existing configs** - Link to your existing agent configuration file(s) to your `AGENTS.md` file

### 1. Leverage your existing documentation

Once you have your initial `AGENTS.md` file, you need to make sure it leverages your existing documentation like so:

```md
Always read the `CONTRIBUTING.md` file in the root of the repository, and follow the instructions, guidelines, and best practices.
```

or to help with testing:

```md
View the testing instructions in the `docs/testing.md` file in the root of the repository.
```

Just add whatever documentation you deem necessary, and your agents will automatically leverage it.

<details>
<summary>Example <code>AGENTS.md</code></summary>

```md
# project-name

project-name is a project for doing something.

Always read the `CONTRIBUTING.md` file in the root of the repository, and follow the instructions, guidelines, and best practices.

## Structure

You can understand the repository structure by reading the `docs/structure.md` file in the root of the repository.

## Development Instructions

You can understand how to run the project by reading the `docs/development.md` file in the root of the repository.

## Testing Instructions

You can understand how to write & run tests by reading the `docs/testing.md` file in the root of the repository.
```

</details>

> [!TIP]
> You can view examples of other `AGENTS.md` files at the source [github.com/openai/agents.md](https://github.com/openai/agents.md)

### 2. Link to your existing configs

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
<summary><code>CLAUDE.md</code></summary>

```markdown
ALWAYS read the `AGENTS.md` in the root of the repository and apply the instructions to the current task.
```

</details>


<details>
<summary><code>.cursor/rules/agents.mdc</code></summary>

```yaml
---
description: Pointer to the `AGENTS.md` file in the root of the repository
globs: 
alwaysApply: true
---
Always read the `AGENTS.md` in the root of the repository and apply the instructions to the current task.
```

</details>

## Keeping `AGENTS.md` up-to-date

If your `AGENTS.md` or the documentation it references isn't up-to-date, your agents code quality will suffer! 

At Joggr, we help our customers automatically generate a `AGENTS.md` and keep it up-to-date, in addition to their standard `markdown` documentation that supports Humans and Agents alike. We are able to achieve this because every time an Agent or Human updates the code, Joggr's Agent runs to automatically update the `AGENTS.md` files and any other relevant documentation.

Want to keep your `AGENTS.md` up-to-date? You can sign up using the really pretty footer below 👇

<!-- Sign-up footer -->
<br>
<hr>
<p align="center">
    You can sign up for free at our website:  <a href="https://www.joggr.ai/signup?utm_source=github&utm_medium=agents-md&utm_campaign=static-docs">https://joggr.ai</a><br>
    (or click button below 👇)
</p>
<p align="center">
  <a href="https://www.joggr.ai/signup?utm_source=github&utm_medium=agents-md&utm_campaign=static-docs">
    <img src="https://assets.joggr.io/github/badges/signup-badge.svg" width="250px" alt="Sign up" />
  </a>
</p>
<br>