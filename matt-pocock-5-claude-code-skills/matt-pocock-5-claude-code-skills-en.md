# Lecture Notes: Claude Code 5 Daily Skills (Matt Pocock)

## 1. Main thesis
For effective management of an AI agent like Claude Code, the developer needs a clear process — **Process-Driven Development**. Instead of random prompts, Matt uses five strictly structured custom commands ("skills") as rigid rails at different stages: from aligning the idea to refactoring architecture.

---

## 2. Five daily skills

### 1. `/grill-me` (Interrogation)
* **Goal:** Eliminate misunderstanding (*misalignment*) at the start of the task.
* **How it works:** The model does not start writing code. It aggressively interviews the developer, asking 40 to 100 sequential questions, exploring all branches of design decisions and revealing hidden dependencies.
* **Result:** A shared mental model (*design concept*) before work begins.

### 2. `/write-a-prd` (Requirements generation)
* **Goal:** Capture the results of the interrogation in a final destination document.
* **How it works:** AI collects all answers from the `/grill-me` session and packs them into a structured Product Requirements Document (PRD).
* **Result:** A ready markdown file containing user stories, technical constraints, architectural decisions, and acceptance criteria.

### 3. `/prd-to-issues` (Kanban breakdown)
* **Goal:** Decompose a monolithic PRD into independent atomic tasks.
* **How it works:** It splits a large feature into small tickets, strictly following the rule of **vertical slices**. The tasks are placed onto a local Kanban board as markdown files.
* **Result:** An optimal pool of tasks prepared for parallel or sequential work by AI agents in AFK mode.

### 4. `/tdd` (Test-driven development)
* **Goal:** Maintain control over the code while AI writes it.
* **How it works:** It forces AI to follow the Red-Green-Refactor cycle. The model must first write a failing test, run it, confirm the failure, and only then implement the code.
* **Result:** Reliable protection against LLM cheating and automatic coverage of the system with quality tests.

### 5. `/improve-codebase-architecture` (Deepening modules)
* **Goal:** Fight entropy and chaotic file fragmentation.
* **How it works:** It scans the project for tightly coupled shallow components and proposes rebuilding them into deep modules with powerful internal logic and a very simple external interface.
* **Result:** The codebase becomes easy to test, and interfaces become understandable to both humans and AI.

---

## Main takeaway
These five skills turn AI from an unpredictable text generator into a disciplined, predictable engineer. The human's job is to act as a strategic architect: direct `/grill-me`, control interfaces with `/improve-codebase-architecture`, and run feedback loops.

## Links
- https://www.youtube.com/watch?v=EJyuu6zlQCg
