LLMs use tools to complete tasks through the ReAct loop with the help of context, but this also exposes obvious vulnerabilities: models may hallucinate (fabricate nonexistent tools or parameters), select the wrong tools, or fail to recover on their own when encountering errors. There is a huge gap between a working demo and a reliable product, and these vulnerabilities are precisely the problems that Harness engineering aims to solve.

As mentioned earlier: Agent = LLM + Context + Tools. From the perspective of Harness engineering, the LLM can be abstracted as the core component, Model, while the code, configurations, and services within the Agent boundary that support model execution and interactions between the model and the environment can be collectively referred to as the Harness. These two perspectives are not substitutes for each other, but descriptions of the same Agent implementation at different levels of abstraction. The core of the Harness consists of "context management + tool interfaces" from the original formula, plus three layers of safeguards: constraints (defining what the Agent can and cannot do), validation (checking whether the Agent has done things correctly), and correction (determining how to recover when something goes wrong).

**Complete composition:**

Agent = Model + Harness

Harness = Context Management + Tool Interfaces + Constraints + Validation + Correction

Agent ↔ Environment

A minimal demo only requires a Model and a Harness capable of constructing context and exposing tools. A production system also needs to incorporate constraints, validation, and correction within the same boundary. For example, a refund Agent can place refund policies in context, constrain tool calls through permission and amount rules, validate results using database states, and retry or roll back when timeouts occur. Harness engineering focuses precisely on this layer of execution and governance code that exists "outside the model but inside the Agent boundary."

More precisely, the Harness is not everything outside the model, but the execution and governance layer that exists within the Agent boundary and outside the model. It is responsible for coordinating interactions between the Model and the Environment, but does not include the environment itself. Tool definitions, calling adapters, and sandbox permission and reset mechanisms belong to the Harness; files and processes that change as actions are performed inside the sandbox, external databases, web pages, users, and the physical world belong to the Environment. Physical deployment location also does not determine conceptual ownership—even if a simulated environment and the Agent run within the same process, it is still the Environment. The core of the Harness is context management and tool interfaces.

Early Agent frameworks mainly focused on context and tools: providing models with tools and context so that they could "do things." However, the focus of production-grade Agent systems has shifted toward constraints, validation, and correction: ensuring that tool calls are safe, context is properly managed, and errors can be corrected.

Taking Claude Code as an example, most of the code in its Harness is devoted to constraints, validation, and correction rather than context and tools. The tools themselves (file reading and writing, command execution, and search) account for only a small portion, while the safeguard mechanisms built around these tools are the real core. These mechanisms include:

- **Workflow State Management:** Tracking which step the Agent is currently executing.

- **Multi-Level Context Compression:** Automatically condensing information when the context becomes too large.

- **Permission Classification:** Controlling which operations require user confirmation.

- **Circuit Breaker:** Automatically stopping retries when errors occur consecutively—just like a circuit breaker in a home electrical system trips during a short circuit to prevent the entire system from failing.

- **Error Recovery Mechanisms:** Catching exceptions, rolling back to the previous stable state, retrying, or handing control back to a human.

The industry is shifting from "being able to do things" to "being able to do things reliably." Harness engineering has therefore become a core competitive advantage of Agent systems.
