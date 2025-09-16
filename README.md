# `joggr/agents.md`

A standard for configuring a universal [`AGENTS.md`](https://github.com/openai/agents.md) that supports all of your codegen agents, and leverages your existing documentation to improve the quality of generated code.

[View the standard](./STANDARD.md)

## Why?

### 📖 Great documentation improves the quality of generated code

At Joggr, we have been working with our customers to automatically generate a `AGENTS.md` and keep it up-to-date, in addition to their standard `markdown` documentation. We've seen significant improvements in the quality of generated code when a repository has great documentation, but you also need to make sure your agents KNOW about those great docs.

### 🙌 `AGENTS.md` is not supported by all agents

Not all agents will automatically look for a `AGENTS.md` file in the root of the repository, for example tools like `cursor`, `claude`, etc. have their own configuration files.

### 💸 Save time and money with pre-configured context

By pre-configuring great context for all of your agents, they are not required to `grep` or `ls` through your repository to find the relevant documentation, files, or other context needed to complete their tasks.

## Who?

Below are some examples of repositories using the `joggr/agents.md` standard:

- [viteval](https://github.com/viteval/viteval/blob/main/AGENTS.md) - A framework for evaluating LLMs using TypeScript powered by Vitest
- [VoltAgent](https://github.com/VoltAgent/voltagent/blob/main/AGENTS.md) - A TypeScript framework for building AI Agents

[View examples](./examples)

## How to I maintain my `AGENTS.md` & documentation?

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
