# Lecture Notes: AI Coding Workflow (Matt Pocock)

## 1. Main Lecture Thesis
When we say AI is a new paradigm in development, we often forget that **fundamental software engineering principles** (the ones that matter for working in teams) also work perfectly when interacting with AI. Code quality directly impacts AI agent performance: a messy codebase always produces worse results.

---

## 2. LLM Limits: "Smart" and "Dumb" Zones

When working with large language models, it is important to understand the concept of context zones:

* **Smart Zone:** At the start of the conversation, when context is clean, the AI works most effectively because attention connections are not overloaded.
* **Dumb Zone:** As tokens are added to the context, the model's attention scales quadratically. Whether the context limit is 200k or 1M tokens, after roughly **100k tokens** the model starts to become "dumb" and make bad decisions.

> **Conclusion:** Tasks for AI should be split so they remain within the *Smart Zone*.

---

## 3. Critique of "Compacting" and "Specs-to-Code"

* **The compacting problem:** Many developers like to compress chat history (create a short summary of the session) to free up context. Matt dislikes this approach. He prefers fully clearing the context and returning to the base system prompt, because that state is always predictable and stable.
* **The "Specs-to-Code" problem:** The idea of writing only requirements, handing them to AI, and editing the requirements instead of the code (*vibe coding*) fails in practice. The developer must stay in control, understand the architecture, and personally manage the code.

---

## 4. Workflow Stages (Division of Work)

All tasks in the development process fall into two categories:
1. **Human-in-the-loop:** Tasks that require deep human involvement (design, alignment).
2. **AFK (Away From Keyboard):** Tasks that can be fully delegated to AI.

### Stage A: Alignment with the "Grill Me" skill (*Human-in-the-loop*)
Instead of asking AI to immediately write an implementation plan, Matt uses the prompt skill **"Grill me."**
* **Idea:** AI aggressively and sequentially asks the developer questions about the requirements, highlighting blind spots (for example: *"Should gamification points be awarded retroactively for old lessons?"*).
* **Result:** Achieves a shared mental model of the task (*design concept*) between the human and the AI.

### Stage B: Building PRD and Kanban board (*Human-in-the-loop*)
After the "grill" stage, AI generates a **PRD (Product Requirements Document)** — a destination document describing where we are going — which is then broken down into tasks for a **Kanban board** (the journey describing how we get there).

* **Vertical slices rule:** AI loves coding "horizontally" (first the database, then the API, then the frontend). This is bad because feedback arrives too late. You need to force AI to build thin vertical slices (for example: schema change + minimal service + dashboard display in one step) so you can see working results sooner.
* A Kanban board should be structured as a directed acyclic graph (DAG), so independent tasks can be **parallelized** across AI agents.

### Stage C: AFK Implementation (*Night Shift*)
Tasks from the Kanban board are given to an autonomous AI worker (scripts based on `Claude Code` or solutions like `Sand Castle`). The cycle runs:
1. AI takes a task from local markdown files.
2. Applies **TDD (Test-Driven Development):** writes a failing test first (*Red*), then writes code to make the test pass (*Green*). TDD prevents AI from cheating by writing poor tests after the fact.
3. Runs feedback loops: tests, linters, TypeScript type checks. Without automated checks, AI codes blindly.

---

## 5. Preparing the Codebase for AI: Deep Modules

If AI produces bad code, the problem should be searched for in project architecture. According to John Ousterhout's book *A Philosophy of Software Design*, modules are of two types:

* **Shallow Modules:** Many small files with lots of cross-connections. AI gets confused in them, and tests require lots of mocks. If not managed, AI will build exactly this structure.
* **Deep Modules:** Modules that expose a very small and simple public interface (API), while hiding a lot of internal complexity.

> **Matt's strategy:** The human developer should design the interfaces of these deep modules, while the internal implementation (which becomes a comprehensible "gray box") can safely be delegated to AI.

---

## 6. Enforcing Coding Standards (Push vs Pull)

When managing agents, there are two approaches to giving instructions:
* **Push:** Forcing AI to consume rules (for example, via `claude.md`). This consumes context. Matt recommends using Push only during **automatic code review**, which runs in a clean context after code is written (for review, use a smarter model like Claude 3 Opus).
* **Pull:** Storing standards as local "skills" (repository instructions) that the AI developer (for example, Claude 3 Sonnet) can read on demand.

---

## Main takeaway
Don't try to automate everything (idea, code, QA), or you will end up with faceless AI sludge (*slop*). Human control, taste, and manual QA are irreplaceable.

The best instructions for managing modern AI agents are found in classic software engineering books written long before the age of artificial intelligence.

## Links
- https://www.youtube.com/watch?v=-QFHIoCo-Ko
