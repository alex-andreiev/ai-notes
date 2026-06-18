# Lecture Notes: Agentic AI Workflows (Andrew Ng, DeepLearning.AI)

## 1. Main thesis
The main driver of progress in AI today is not just increasing base LLM parameters, but the shift from the Zero-shot paradigm (asking the model to answer in one pass) to **Agentic Workflows**. Letting AI iteratively reason, find mistakes, collect feedback, and refine its own code (similar to how a human programmer works) delivers a dramatic quality improvement even on relatively older models.

---

## 2. Four key agent design patterns

Andrew Ng identifies four basic design patterns that underpin effective AI agents:

### 1. Reflection
* **Essence:** Instead of immediately accepting the model's first answer, the system forces AI to critically evaluate its own result.
* **How it works:** Model A generates code, then prompt or another agent B is asked: "Carefully inspect this code for bugs, inefficient syntax, and missing edge cases, then propose improvements." The model rewrites its own code based on the feedback.

### 2. Tool Use
* **Essence:** Extend the LLM's capabilities by giving it external tools for analysis, computation, and data gathering.
* **How it works:** If the model needs to do complex math, run tests, or fetch current information, it emits arguments for external function calls (Code Interpreter, Web Search, databases) and consumes the results as input for the next generation step.

### 3. Planning
* **Essence:** The ability to decompose a complex, abstract goal into a sequence of understandable steps.
* **How it works:** The agent first generates a high-level action plan (for example: "Step 1: Review API docs structure; Step 2: Write a test skeleton; Step 3: Implement logic"), then executes it serially, adjusting steps as external conditions change.

### 4. Multi-agent Collaboration
* **Essence:** Split a complex task among multiple agents, each with a unique system role (persona).
* **How it works:** The workflow is configured so that one agent acts as "Product Manager" (writes requirements), another as "Engineer" (writes code), and a third as "Tester" (writes and runs tests). Their dialogue and mutual revisions produce a much more robust final outcome.

---

## 3. A pragmatic take on token generation speed
The shift to agentic workflows changes infrastructure and latency expectations:
* In Zero-shot, developers demand instant responses (low latency).
* In Agentic Workflows, we sacrifice immediate response: AI may generate thousands of tokens in the background, think, run tests, and rewrite code over 5–10 minutes (AFK / Night Shift mode).
* **Conclusion:** Getting working, polished code after 10 minutes of agent iterations is much more valuable than getting mediocre, non-working code in 3 seconds.

---

## Main takeaway
Prompt engineering has evolved into agent system engineering. Understanding fundamental patterns (Reflection, Tool Use, Planning, Multi-agent) enables developers to build flexible, autonomous AI pipelines. The human's job is to set high-level rules, decompose complex business context, and control the final acceptance points of the system.

## Link
- https://www.youtube.com/watch?v=MzWIIlx0Gpc
