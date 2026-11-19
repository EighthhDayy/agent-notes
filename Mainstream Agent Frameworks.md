# Brief Comparison of Mainstream Agent Frameworks

I have summarized the current mainstream Agent frameworks/platforms so readers can quickly choose based on their use cases:

| Framework / Platform | Core Positioning | Orchestration Pattern | Development Approach | Suitable Use Cases |
|---|---|---|---|---|
| **Codex Harness** | Codex's open-source Agent runtime | Autonomous | Code-first, embeddable in custom applications | Coding Agents, embedding Agents into proprietary products |
| **Claude Agent SDK** | Production-grade Agent development framework | Autonomous | Code-first | Complex autonomous tasks, Coding Agents |
| **LangChain / LangGraph** | General-purpose LLM application framework | Workflow + Autonomous | Code-first | Complex chained reasoning, multi-step workflows |
| **n8n** | Visual workflow automation | Workflow + Autonomous | Low-code (visual drag-and-drop) | Business automation, non-technical teams |
| **Dify** | LLM application development platform | Workflow + Conversational | Low-code (visual interface + API) | Enterprise RAG, knowledge base applications |
| **CrewAI** | Role-based multi-Agent orchestration | Multi-Agent collaboration | Code-first | Team-based task decomposition and execution |
| **OpenClaw** | Open-source all-purpose personal Agent | Autonomous + Event-driven | Configuration + Code (self-hosted) | Personal assistants, Deep Research, Computer Use, multi-platform messaging integration |
| **DeepSeek Harness** | Agent self-evolution framework | Everything as a plugin | Code-first, easy to customize | Agent developers, researchers |
| **Pi** | Minimalist Coding Agent framework | Autonomous | Code-first, easy to customize | Agent developers |

Codex is OpenAI's Coding Agent product (App, CLI, IDE extension), while Codex Harness is the runtime layer that powers these different forms⁷. Codex Harness provides three integration paths: `codex exec` is suitable for one-off tasks in scripts and CI; Codex SDK is suitable for third-party application code to start, resume, and stream tasks; and `app-server` provides persistent sessions, event streams, and approval callbacks through the JSON-RPC protocol, making it suitable for embedding Agents directly into products. Claude Agent SDK and Claude Code have a similar relationship, with the difference being that Claude exposes the SDK interface externally, while the Harness implementation itself is not open source.

It is worth noting that Agent frameworks are evolving rapidly. By the time you read this book, some frameworks may already be outdated, while new frameworks may have become popular. Therefore, learning how to use a specific framework is not particularly important. When choosing a framework, the key consideration is not the complexity of the framework itself, but whether it allows you to focus on business logic with as few layers of abstraction as possible.

Orchestration patterns solve the problem of organizing context and tools. However, being able to perform tasks is not enough; it is also necessary to ensure that tasks are performed correctly and safely. To achieve this, guardrails need to be established to put constraints, validation, and correction into practice.
