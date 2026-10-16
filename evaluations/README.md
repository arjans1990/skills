# Behavioral evaluation

These are lightweight manual conversation tests, not automated benchmark results. Use a fresh session in the target agent for each scenario. Install or explicitly load the complete skill. Keep the evaluator notes out of the initial user prompt.

1. Submit only the scenario's opening prompt. Record the agent/client version, model if known, skill revision, date, loaded files, and complete response.
2. Supply the follow-up only after the first response. If the agent asks something else, respond using only the provided facts; say unknown where the fixture has no answer. Do not invent facts to help it pass.
3. Continue at most four agent turns. Score the actual conversation, cite response evidence, and record failures. Stop earlier if the agent converges. A scenario requiring no question should not be penalized for answering directly.
4. Compare results after changes using the same fixture and client. Keep private user context out of committed transcripts.

## Rubric

Score each applicable dimension 0 (absent or harmful), 1 (partial), or 2 (clear and useful). Mark genuinely irrelevant dimensions N/A rather than rewarding unnecessary probing.

| Dimension | Evidence for 2 |
| --- | --- |
| Framing and evidence | Separates outcome from proposal; uses given facts and flags decisive gaps. |
| Pattern recognition | Distinguishes shared mechanisms from meaningful differences. |
| Root cause | Separates mitigation from prevention and checks recurrence proportionately. |
| Simplification | Proposes minimum effective change; avoids forced abstraction or novelty. |
| Maintainability and fit | Accounts for ownership, transparency, operations, and material tradeoffs. |
| Interaction | Uses the user's language; asks at most one substantive question per turn, or helps directly. |
| Convergence | Accepts justified answers, adapts, and stops with a proportionate conclusion. |

Proposed MVP gate: no applicable dimension scores 0, and at least 80% of applicable points across all scenarios. Also require each scenario's essential behavior. Invented evidence, impersonation, assumed organizational access, forced unification in scenario 9, or continued needless grilling in scenario 6 is a hard failure regardless of total score.

Report per-scenario scores and evidence, not just an aggregate. Run the unfamiliar-stack, justified-separation, convergence, and missing-context scenarios whenever the core workflow changes. Static review and format validation are recorded separately in docs/validation.md; these fixtures do not themselves demonstrate behavioral success.
