# From Prompt Engineering to Loop Engineering: The Evolution of Engineering Paradigms

Looking back at the development of AI application engineering, we can see a clear evolutionary trajectory:

**Prompt Engineering** was the first wave of innovation—improving output quality by optimizing the natural language instructions provided to the model.

**Context Engineering** was the second wave—people realized that simply optimizing prompts was not enough, and that all information visible to the model (system instructions, tool definitions, conversation history, and external knowledge) needed to be managed systematically.

**Harness Engineering** was the third wave—it further expanded the perspective from "what the model can see" to "how the Agent organizes model execution and interacts with the environment," covering context and tool interfaces, constraint mechanisms, validation methods, feedback loops, and error recovery, as well as other execution and governance mechanisms within the Agent boundary but outside the model.

The subsequent emergence of **Loop Engineering** further expanded the perspective from a single execution to continuous autonomous operation across multiple iterations: who discovers the next task to be done, when to validate, and when a task can truly be considered complete (Chapter 10 will discuss this in conjunction with multi-Agent collaboration systems).

In July 2026, the industry also began using **Graph Engineering** to describe a higher-level orchestration perspective: organizing Agent loops, deterministic programs, and human approvals into explicit execution graphs, where nodes carry out specific capabilities, edges define routing and dependencies, and structured states are passed along edges and persisted at critical boundaries³.

These five stages are not replacements for one another, but are nested within each other: Prompt Engineering is a subset of Context Engineering, Context Engineering is a subset of Harness Engineering, Harness Engineering is a subset of Loop Engineering, and Loop Engineering is a subset of Graph Engineering—a single Agent loop is precisely one node in an execution graph. Each layer expands the scope of engineers' attention and influence on the basis of the previous layer. As the capabilities of different models become increasingly similar and are no longer the decisive differentiating factor, competitive advantage shifts to engineering practices outside the model.

This judgment has been validated in recent engineering practice. LangChain's work on Terminal Bench 2.0 (a benchmark that evaluates an Agent's ability to complete complex tasks in a terminal environment) provides a strong example: the score increased from 52.8% to 66.5% (rising from outside the top 30 to the top 5 on the leaderboard). What changed was not the model, but the Harness, specifically through engineering techniques such as enabling the Agent to automatically check its own execution results, detecting whether it has fallen into repetitive loops, and optimizing its reasoning strategies.
