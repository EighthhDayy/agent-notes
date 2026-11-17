#Workflow Pattern: Deterministic Orchestration

A **Workflow** is a system that orchestrates LLMs and tools through predefined code paths. Its execution path is deterministic and designed in advance by developers—what to do at each step and where to go next are all hard-coded, while the LLM is only responsible for understanding and generation within each node.

Taking a flight booking Agent as an example, a workflow can be designed with four fixed nodes:

1. **Verify User Identity** — Call an authentication API to confirm the user's identity.
2. **Search Available Flights** — Query the flight database based on the user's requirements.
3. **Complete Payment** — Call the payment interface to process the payment.
4. **Confirm Booking** — Call the booking API to reserve seats and send confirmation information to the user.

Each node can use an LLM internally (for example, to understand the user's travel requirements through natural language), but the order of transitions between nodes is fixed by code—the system will not book seats before payment is completed, nor will it begin searching for flights before identity verification.

The workflow pattern has two core advantages. The first is **strict process control**: developers can ensure that critical steps are not skipped or executed out of order. For example, business rules such as "booking is not allowed before payment" are enforced through code rather than relying on the LLM's judgment. The second is **security**: because the execution path is deterministic, prompt injection or model errors can at most affect processing within the current node and cannot cause the Agent to jump to branches that should not be executed—the attack surface is limited to a single node.

The main limitation of workflows is **lack of flexibility**. When situations arise that are not covered by the predefined process (for example, a user suddenly wants to change their flight during payment, or a flight is unexpectedly canceled and alternative options need to be recommended), the fixed node path cannot respond flexibly. The system can only follow predefined exception-handling branches or return control to a human.

Consider one of the simplest workflow examples: **text-to-image generation**. Users often express their requirements in a single sentence of everyday language, such as "Draw me a scene showing what programmers' work looks like after AGI is achieved." However, text-to-image models such as Stable Diffusion only accept prompts in a specific style—comma-separated English tags, quality terms, and negative prompts. Therefore, the workflow needs to arrange two fixed nodes between the user and the image generation model:

1. **Prompt Rewriting** — Use an LLM to rewrite the user's natural language requirements into the prompt format preferred by the text-to-image model. For the example above, "what programmers' work looks like after AGI is achieved" is a very broad requirement, so the LLM also needs to think carefully (for example, "After AGI is achieved, programmers no longer need to write code, so the image should depict a programmer sunbathing on a beach while directing AI employees through a brain-computer interface"), and then provide a specific scene description.

2. **Image Generation** — Use the rewritten prompt to call the text-to-image model and generate an image.

The execution path is hard-coded. The LLM node in this workflow performs **translation**, converting human language into an input format that the tool can understand. It exists because the text-to-image model "cannot understand human language." This kind of Harness code, specifically designed to compensate for the capability limitations of tools (or models), can be called an **adaptation layer**.

However, if the image generation tool is replaced with a multimodal model that has native image generation capabilities, such as Nano Banana 2 or GPT-Image 2, prompt rewriting is no longer necessary. Regardless of how the user describes the request, the model can understand it directly and generate the image.

### Experiment: Comparison Between Text-to-Image Workflows and Native Image Generation

Let the same natural language request follow two different paths.

**Workflow Path:** The LLM first rewrites the request into a Stable Diffusion-style prompt, then calls the text-to-image model to generate the image.

**Native Path:** Send the original sentence directly to a multimodal model that supports native image generation (such as GPT-Image 2), generating the image in a single call.

Compare how the prompt rewriting node transforms the original request, and which of the two paths produces an image that more closely matches the original requirement.

It is worth comparing two types of requests: one with specific descriptions (such as specifying the text on a poster), and another with broad descriptions (such as the AGI workplace scenario above). For the latter type, the workflow path may still have its own advantages.

This experiment demonstrates that **the parts of the Harness that compensate for limitations in model capabilities will be internalized by the models themselves as models become stronger.** Few-shot examples and prompt techniques such as "let's think step by step" have been internalized by instruction fine-tuning and reasoning models; output format repair and JSON parsing error tolerance have been internalized by structured outputs and native tool calling; prompt rewriting for text-to-image generation has been absorbed by models' native multimodal understanding and generation capabilities. Each round of internalization eliminates adaptation-layer code such as "translation" and "scaffolding."
