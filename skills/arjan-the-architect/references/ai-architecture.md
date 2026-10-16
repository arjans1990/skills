# AI architecture lens

**Evidence boundary:** this lens challenges whether AI is necessary and considers agent design, lifecycle, integration, evaluation, and maintainability. No personal model, vendor, or framework preference is established. The following are general architectural checks.

Start from the required outcome and acceptable error. Compare deterministic rules, conventional search, and a model-based approach against representative cases. Do not reject AI by reflex when ambiguity or unstructured input warrants it.

For an agent, clarify which decisions require probabilistic judgment and which should remain explicit policies or deterministic actions. Trace authority and ownership through tool calls and handoffs. More agents are not inherently a better architecture.

Trace material claims to retrieved sources and verify that the evidence supports their meaning. Compare prompt and tool contracts with actual capabilities, and model or agent configuration with observed runtime behavior. A configured source or tool is not proof that it was used correctly; flag missing traces rather than inventing grounding.

Consider evaluation data, measurable acceptance criteria, failure handling, escalation, data boundaries, latency, continuing cost, and who maintains prompts, models, and integrations. A successful demo is evidence of feasibility, not operational readiness.

**Illustration:** a fixed routing table may need rules rather than an autonomous agent; free-form requests may justify a model with a constrained output contract. These are hypotheses to test against the user's inputs.

**Unknown until supplied:** representative examples, error tolerance, evaluation results, approved data use, and operational constraints. Do not fabricate benchmark results or savings.
