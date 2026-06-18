# Lecture Notes: Vibe Coding in Production (Erik Schultz, Anthropic)

## 1. Main Lecture Thesis
The term **Vibe Coding** (introduced by Andrej Karpathy) describes a process where the developer acts as a product manager or director, and AI writes thousands of lines of code autonomously. But to safely apply vibe coding in real production and avoid technical debt, architectural boundaries must be strictly controlled and results must be verified.

Software systems should be split into critical infrastructure and isolated nodes.

---

## 2. Component Separation: Core Nodes vs Leaf Nodes

For successful AI agent scaling, Anthropic recommends classifying architectural elements in the codebase into two groups based on dependencies (In-Degree / Out-Degree):

* **Core Nodes:**
  * Components that many other parts of the system depend on (high In-Degree). These include critical infrastructure, shared services, databases, and security systems.
  * **Rule:** Automation is dangerous here. Changes in Core Nodes require mandatory manual design and strict human code review, because the cost of failure is enormous.
* **Leaf Nodes:**
  * Isolated components with low dependency levels (low In-Degree). These are end features, specific business logic at the "edges" of the application, and independent services.
  * **Rule:** This is the ideal zone for full AI autonomy. Leaf Nodes can be handed to AI agents as turnkey work for fast, large-scale code generation.

---

## 3. Framework Limits and the "Simple Agents" Pattern

Anthropic’s experience working with dozens of teams in the industry revealed an important pattern:
* **Problem with complex frameworks:** Developers often try to use heavy, rigid agent frameworks and specialized libraries. This makes the system brittle and unpredictable.
* **Solution — Simple composite patterns:** The most successful implementations use simple, easily composable workflows (prompts, hooks, basic call loops) that are easy for a human developer to control, debug, and tune.

---

## 4. The Engineer’s Role as an AI Product Manager

When working with tools like `Claude Code`, the developer shifts from "writing lines of code" to directing AI:
1. **Asking the right questions:** Formulating clear high-level requirements and decomposing tasks.
2. **Managing context:** Providing the agent with the right documentation, types, and architectural constraints at the right time.
3. **Strict verifiability:** Automated tests are the main success criterion for AI work. If a Leaf Node’s code is covered by passing tests, the developer can trust the AI’s autonomous implementation.

---

## Main takeaway
Vibe coding in production is possible and effective if you act as a responsible architect. Delegate routine work to AI in isolated Leaf Nodes, but keep manual strategic control over the system core (Core Nodes) and always require AI to write tests for verification.

---

## Source
- https://www.youtube.com/watch?v=fHWFF_pnqDk
