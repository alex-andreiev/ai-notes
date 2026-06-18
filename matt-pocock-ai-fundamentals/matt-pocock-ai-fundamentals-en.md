# Lecture Notes: Fundamental Development Principles Matter More Than Ever (Matt Pocock)

## 1. Main Lecture Thesis
In the age of AI, many developers begin to doubt the value of their skills, thinking that old rules no longer apply. However, **fundamental software design principles** matter now more than ever.

AI is excellent as a tactical executor (a programmer on the ground), but it critically needs a strategist — a human developer who manages the architecture.

---

## 2. Critique of the "Specs-to-Code" Concept and Code Pricing
* **The illusion of "Specs-to-Code":** The popular movement claims you can write only specifications (requirements), feed them to an AI compiler, and get a finished application without looking at the code. In practice, repeatedly restarting AI without code control leads to accumulating software entropy — the system tends toward chaos, quality drops with each iteration, and the result becomes garbage.
* **Code is NOT cheap:** The phrase "code now costs nothing" is wrong. Bad code has become the most expensive asset in history because in a tangled, fragile, and dirty system AI agents cannot work properly. Conversely, clean and understandable architecture allows you to get the maximum value from AI capabilities.

---

## 3. Failure Modes When Working with AI and Their Solutions

### Failure Mode #1: AI does not do what was expected
* **Cause:** Communication breakdown and lack of shared vision. According to Frederick Brooks' book *The Design of Design*, there must be a mental, ephemeral understanding of the system between designers — a **design concept**. This is not a physical document, but a shared idea of the product.
* **Solution (The "Grill Me" prompt skill):** Before giving AI code or a plan, launch the interrogation skill. AI is forced to relentlessly interview the developer (asking 40–100 questions) until shared task understanding is reached. This is far more effective than standard "plan mode" in tools like Claude Code.

### Failure Mode #2: AI becomes too verbose
* **Cause:** Lack of a shared terminology between you and the model.
* **Solution (Unified language from DDD):** Eric Evans in *Domain-Driven Design* describes the concept of **Ubiquitous Language**. Matt created a skill that scans the codebase, extracts key domain terms, and generates markdown tables. This file is always open during planning and coding, which forces AI to extract context without extra fluff and follow the requirements.

### Failure Mode #3: AI produces code that simply does not work
* **Cause:** AI "outruns your headlights" — writing huge chunks of code without intermediate validation. Development speed should be limited by feedback loop speed.
* **Solution (Mandatory TDD):** Use Test-Driven Development. AI must first write a failing test (Red), then the minimal code to make it pass (Green), and only then refactor.

---

## 4. Architectural Requirement: Deep Modules

For feedback loops and TDD to work effectively, the codebase itself must be easy to test. John Ousterhout in *A Philosophy of Software Design* divides modules into two types:

* **Shallow Modules:** Many small files/functions with bloated interfaces and complex dependencies. AI loves to build this structure, but it gets confused in it over long-term maintenance.
* **Deep Modules:** A relatively small number of large modules that hide huge functionality and complexity behind a **very simple external interface**.

> **Engineering trick to save brain resources:** The human developer focuses all attention on designing and strictly controlling the external interfaces of deep modules. Internal implementation can be fully delegated to AI and treated as a "gray box" (with good boundary tests). This preserves sanity and prevents memory overload as the project grows quickly.

---

## Main takeaway
Invest in system design every day (a lesson from Kent Beck). AI is a fantastic tactical tool, but without your strategic architectural vision and knowledge of fundamental development principles, the codebase will inevitably turn into chaos.

*All mentioned prompts and skills from Matt are available in his public repository `mattpocock/skills`.*

---

## Links
- https://www.youtube.com/watch?v=v4F1gFy-hqg

## Sources
- Matt Pocock public repo: `mattpocock/skills`
- Books: Frederick Brooks, Eric Evans, John Ousterhout, Kent Beck
