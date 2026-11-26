# Part One Summary

This chapter started from practical experience and established the basic framework for understanding and building AI Agents.

**Agent = Brain + Eyes + Hands and Feet:** The LLM is the brain (the decision-making core), context is the eyes (determining what it can see), and tools are the hands and feet (determining what it can do). All three are indispensable.

**Expanding the Eyes and Hands and Feet Is the Most Important Capability Lever:** With the model held constant, redefining or expanding the observation space and action space—that is, expanding context and tools—can often make tasks that were previously incomprehensible directly understandable. The evolution of Manus and OpenClaw both demonstrates that generality largely comes from the expansion of interface boundaries; such expansion must be done as needed, together with permission controls and validation.

**Eyes (Context) Are the Decisive Factor:** Context consists of a static prefix (system prompts + tool definitions) and a dynamic trajectory (message history). Ablation experiments show that the components are not equally important: removing tool definitions or tool execution results directly takes away the ability to act and complete the loop, while the cost of removing the other two depends on whether the information can be reconstructed from current observations. The essence of the ReAct loop is to continuously append to the trajectory so that the model can keep advancing the task.

**Harness Is Where the Competitive Advantage Lies:** Model capabilities are becoming commoditized, and **the real differentiation lies in the Harness—constraints, validation, and correction mechanisms built around context and tools to ensure that Agents can "do things reliably."** In production-grade Agent systems, the vast majority of Harness code implements these safeguards rather than context and tools themselves.

**From Workflows to Autonomous Agents:** Optimize prompts first, then consider workflows, and only introduce autonomous Agents as a last resort—this is the most practical order for reducing unexpected risks. Each orchestration pattern has its applicable scenarios; there is no universally optimal solution.

**Five Design Patterns Run Throughout the Book:** Proposer–Reviewer, Progressive Disclosure, Append-Only, Boundary Set + Retained Set, and Minimal Diff + Rollback.

**Security Is an Architectural Issue:** Security issues must be considered from the first line of code rather than patched after deployment. **Guardrails are divided into three layers according to how difficult they are to bypass: the Context Layer, Execution Layer, and Data Layer.** The security discussions in subsequent chapters are organized around this framework.
