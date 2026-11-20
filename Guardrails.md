# Guardrails and Security

**Guardrails** form a layered defense to ensure that Agent behavior is safe and controllable. They can be used to manage data privacy risks (such as preventing system prompt leakage) or reputational risks (such as ensuring that model behavior aligns with brand identity). In practice, guardrails can first be established for identified risks, and additional guardrails can be gradually added as new vulnerabilities are discovered. 

A single guardrail is unlikely to provide sufficient protection. Only by combining multiple specialized guardrails can a more resilient Agent system be built.

Guardrails also have another type of failure: **false refusals**. To reduce the probability of dangerous requests being allowed, models may also reject some legitimate but seemingly sensitive tasks, such as authorized security testing and model distillation research. Therefore, guardrail evaluation must not only test "whether requests that should be refused are blocked," but also "whether explicitly permitted requests can be completed successfully."
