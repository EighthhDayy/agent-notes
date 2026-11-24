# Human Intervention

**Human intervention** (Human in the loop, also known as human-in-the-loop) is a key safeguard that allows Agents to improve their actual performance without compromising the user experience. This is particularly important in the early stages of deployment, helping to identify failure patterns, discover edge cases, and establish robust evaluation cycles.

Implementing human intervention mechanisms allows Agents to smoothly hand over control when they are unable to complete tasks. In customer service, this means escalating issues to human support agents; for Coding Agents, it means returning control to developers.

There are typically two main situations that trigger human intervention:

**Exceeding Failure Thresholds:** Set upper limits on the number of retries or operations an Agent can perform. If the Agent exceeds these limits, the task should be escalated to human intervention.

**High-Risk Operations:** When operations involve sensitive, irreversible, or high-risk actions, human oversight should be triggered, at least until the team has developed sufficient confidence in the Agent's reliability. Typical examples include authorizing large refunds or payments.
