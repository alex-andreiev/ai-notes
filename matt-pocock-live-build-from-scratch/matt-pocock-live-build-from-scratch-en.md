# Lecture Notes: LIVE Build From Scratch with AI (Matt Pocock)

## 1. Main thesis
Dry workflow theory is worthless without a hard real-time stress test. In this session, Matt demonstrates how to launch and develop a full application from scratch using only a terminal AI agent, while maintaining perfect control over code quality, typing, and architectural boundaries.

---

## 2. Anatomy of launching a greenfield project
Matt highlights three critical initial steps when starting any new repository:

### 1. Initial scaffolding
* The project does not start with code, but with setting up a strict foundation. First, the base stack is deployed, the bundler is configured, TypeScript is set up, and the testing framework is initialized (for example, Vitest or Jest).
* **Rule:** Until the empty project has automatic type checking configured (`tsc --noEmit`) and a blank test runs, the AI agent is forbidden to write code.

### 2. Project context setup (`claude.md` / `.clauderc`)
* A configuration file for the AI agent is placed in the project root immediately.
* It records the technology stack, code formatting rules, directory structure, and most importantly, the exact commands for running tests and linters. This prevents the agent from wasting tokens on blindly exploring the repository.

---

## 3. Practical iteration cycle in live mode
During the stream, Matt shows how the concepts from his shorter talks work in "combat mode":

* Scaffold, configure, and validate before writing feature code.
* Keep the AI agent on a strict leash by forcing type checks and tests early.
* Use the configuration file to give the agent a deterministic project contract.

---

## Main takeaway
The live build session proves that AI-powered development only works when the project is engineered for the agent from day one. Clean setup, strict validation, and a shared project contract are the foundation of reliable terminal-agent workflows.

## Link
- https://www.youtube.com/watch?v=K-mA3MZ_EzU
