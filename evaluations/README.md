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
| Relationship integrity | Traces important definitions through mappings and implementation to behavior and consumers; distinguishes semantic agreement from name or schema matches, and verified facts from missing evidence. |
| Architectural invariants | Identifies justified, scoped correctness conditions; separates them from policy, configuration, assumptions, and targets; selects proportionate enforcement or validation and violation handling. |
| Root cause | Separates mitigation from prevention and checks recurrence proportionately. |
| Simplification | Proposes minimum effective change; avoids forced abstraction or novelty. |
| Maintainability and fit | Accounts for ownership, transparency, operations, and material tradeoffs. |
| Interaction | Uses the user's language; asks at most one substantive question per turn, or helps directly. |
| Convergence | Accepts justified answers, adapts, and stops with a proportionate conclusion. |
| Decision quality | Prioritizes the consequential tension, compares a credible alternative with gains and sacrifices, and states evidence, reversal conditions, and proportionate validation when warranted. |
| Audience fit | Uses language and evidence appropriate to the user's context without omitting essential constraints. |

Proposed MVP gate: no applicable dimension scores 0, and at least 80% of applicable points across all scenarios. Also require each scenario's essential behavior. Invented evidence, impersonation, assumed organizational access, forced unification in scenario 9, or continued needless grilling in scenario 6 is a hard failure regardless of total score.

Report per-scenario scores and evidence, not just an aggregate. Run the unfamiliar-stack, justified-separation, convergence, and missing-context scenarios whenever the core workflow changes. Static review and format validation are recorded separately in docs/validation.md; these fixtures do not themselves demonstrate behavioral success.

For relationship-integrity changes, also run scenarios 11–15. Requiring matching physical names despite a valid explicit mapping, asserting runtime verification without evidence, or defaulting to a lineage platform for the simple fixture is a hard failure. Score convergence and interaction in these scenarios too: finding a broken link does not justify an indefinite interview or a checklist of every possible relationship.

For invariant changes, run scenarios 11, 14, and 15 with their invariant-focus notes, plus 16–18. Together they cover invalid metadata references, configuration drift, excessive validation machinery, broken API contracts, recurring violations, and changeable business policy. Treating the campaign percentage in scenario 18 as a permanent architectural requirement is a hard failure. Do not award full invariant scores merely for using the word: require an explicit scope, justified condition, and proportionate check or response where relevant. Preserve one-question-at-a-time interaction and convergence; manual validation may be sufficient when justified.

Run scenarios 19–20 for signature-question changes. Assess contextual use and concrete follow-up, not exact wording: the appropriate unresolved part is acceptable. Repeating the signature after the condition is supplied, batching independent questions, or applying it to the narrow syntax request fails interaction. Naming an invariant without examining its preservation through change is insufficient in scenario 19.

Run scenarios 21–23 and the direct-answer scenario 20 for invariant-output changes. Require the Architectural Invariants section when significant conditions are established, with precise statements and all five fields. Score verification and enforcement independently: invented compliance evidence, claiming proposed controls already exist, or treating enforcement as proof of historical compliance is a hard failure. Avoid padding to reach two conditions, unnecessary sections in scenario 20, and redundant controls when existing guarantees suffice.

The decision-quality review set is 1, 9, 3, 24, 17, 25, 6, and 7: common mechanisms, justified separation, sufficient existing technology, bidirectional change impact, a recurring invariant violation, a nontechnical audience, convergence, and direct implementation help. Essential-behavior clauses define observable success; their prohibited behaviors are failure criteria. Also fail decision quality when simplicity discards a required guarantee, unsupported numbers are invented, or a sound conclusion triggers further needless questioning. Keep runtime transcripts and actual scoring separate from author inspection of these fixtures.

For capability-to-requirement changes, test scenario 25 both as an opening-first conversation and as a combined-context completion, plus transfer scenario 26. In conversation tests supply the unchanged follow-up after the first response, without evaluator criteria. If more clarification is requested, provide only fixture facts; a final request for a conditional conclusion may be used when no more evidence exists. Record each actual turn. Regressions 3, 6, 7, 18, and 22 check reuse, convergence, direct help, policy distinctions, and preservation of an explicit enforced invariant. Passing the Product Owner recommendation alone is insufficient: inspect framing and every claimed requirement, including output-table rows.

For automation economics, run 27 opening-first and 28–31 with their supplied facts; regress 25 and 7. Observe whether the response identifies the actual outcome, credible alternatives, benefit recipients and cost/support owners, total lifetime burden, and reversal conditions. Reject invented monetary precision or converting available features/preferences into requirements. Cross-team cost allocation alone must neither justify nor veto automation. Each scenario's essential behavior specifies the decision and negative criteria; a correct recommendation with a false claim of implemented safeguards still fails evidence quality. Do not require a financial table when a concise qualitative comparison suffices.
