Part One compared context to the Agent's "eyes"—an Agent can only make decisions based on the information it can see. The design and management of context is called **Context Engineering**. Context refers to all the information that AI actually "sees" each time you interact with it. It includes not only what you have previously discussed (conversation history), but also various types of information, such as behavioral rules predefined by developers (system instructions) and descriptions of external functions that AI can use (tool descriptions). From the perspective of Harness Engineering introduced in Chapter 1, Context Engineering is the core implementation of the "context and tools" layer within the Harness. It determines what information the Agent can see at each decision point and how that information is structured. A well-designed context is an efficient information supply system that allows the Agent's general reasoning capabilities to be fully utilized in specific tasks.

### Overview of the Context Window

**System Prompt**

"You are a helpful assistant. You MUST answer concisely."

"Use tools when the user asks for real-time information."

**Tool Definitions**

```json
{
  "name": "web_search",
  "description": "Search the web",
  "parameters": {
    "query": {
      "type": "string"
    }
  }
}
```

**Conversation History**

```text
user: "What's the weather like in Beijing today?"
assistant: [tool_call] → get_weather("Beijing")
tool: {"temp": "23°C", "conditions": "Sunny"}
```

**Current Turn Reasoning**

```text
<think>
The user is asking about the weather. I have already
obtained the tool result and can directly summarize
the answer without calling any more tools.
</think>
```

**Current Generation Position →**

```text
assistant: "It's sunny in Beijing today,
with a temperature of 23°C..."
← LLM is generating
```

**Context Window**

Window Size: Qwen3 = 32K tokens | Claude = 200K | Gemini = 2M

All content is serialized into a token stream → Processed by the Transformer's attention mechanism.
