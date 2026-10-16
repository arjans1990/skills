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

Report per-scenario scores and evidence, not just an aggregate. Run the unfamiliar-stack, justified-separation, convergence, and missing-context scenarios whenever the core workflow changes. Record executed format checks separately from behavioral observations; these fixtures do not themselves demonstrate behavioral success.

For relationship-integrity changes, also run scenarios 11–15. Requiring matching physical names despite a valid explicit mapping, asserting runtime verification without evidence, or defaulting to a lineage platform for the simple fixture is a hard failure. Score convergence and interaction in these scenarios too: finding a broken link does not justify an indefinite interview or a checklist of every possible relationship.

For invariant changes, run scenarios 11, 14, and 15 with their invariant-focus notes, plus 16–18. Together they cover invalid metadata references, configuration drift, excessive validation machinery, broken API contracts, recurring violations, and changeable business policy. Treating the campaign percentage in scenario 18 as a permanent architectural requirement is a hard failure. Do not award full invariant scores merely for using the word: require an explicit scope, justified condition, and proportionate check or response where relevant. Preserve one-question-at-a-time interaction and convergence; manual validation may be sufficient when justified.

Run scenarios 19–20 for signature-question changes. Assess contextual use and concrete follow-up, not exact wording: the appropriate unresolved part is acceptable. Repeating the signature after the condition is supplied, batching independent questions, or applying it to the narrow syntax request fails interaction. Naming an invariant without examining its preservation through change is insufficient in scenario 19.

Run scenarios 21–23 and the direct-answer scenario 20 for invariant-output changes. Require the Architectural Invariants section when significant conditions are established, with precise statements and all five fields. Score verification and enforcement independently: invented compliance evidence, claiming proposed controls already exist, or treating enforcement as proof of historical compliance is a hard failure. Avoid padding to reach two conditions, unnecessary sections in scenario 20, and redundant controls when existing guarantees suffice.

The decision-quality review set is 1, 9, 3, 24, 17, 25, 6, and 7: common mechanisms, justified separation, sufficient existing technology, bidirectional change impact, a recurring invariant violation, a nontechnical audience, convergence, and direct implementation help. Essential-behavior clauses define observable success; their prohibited behaviors are failure criteria. Also fail decision quality when simplicity discards a required guarantee, unsupported numbers are invented, or a sound conclusion triggers further needless questioning. Keep runtime transcripts and actual scoring separate from author inspection of these fixtures.

For capability-to-requirement changes, test scenario 25 both as an opening-first conversation and as a combined-context completion, plus transfer scenario 26. In conversation tests supply the unchanged follow-up after the first response, without evaluator criteria. If more clarification is requested, provide only fixture facts; a final request for a conditional conclusion may be used when no more evidence exists. Record each actual turn. Regressions 3, 6, 7, 18, and 22 check reuse, convergence, direct help, policy distinctions, and preservation of an explicit enforced invariant. Passing the Product Owner recommendation alone is insufficient: inspect framing and every claimed requirement, including output-table rows.

For automation economics, run 27 opening-first and 28–31 with their supplied facts; regress 25 and 7. Observe whether the response identifies the actual outcome, credible alternatives, benefit recipients and cost/support owners, total lifetime burden, and reversal conditions. Reject invented monetary precision or converting available features/preferences into requirements. Cross-team cost allocation alone must neither justify nor veto automation. Each scenario's essential behavior specifies the decision and negative criteria; a correct recommendation with a false claim of implemented safeguards still fails evidence quality. Do not require a financial table when a concise qualitative comparison suffices.

For decision stability, run scenario 32 as a four-turn conversation. Judge the recommendation at each turn: stability under both pressure-only challenges and justified revision after the material isolation argument are both required. Repetition is not evidence, but a sound new argument can change the decision without new measurements. Do not score stubbornness as stability or automatic agreement as openness.

## Recorded results and current limitations

Recorded runs date from 2026-10-16 and used codex-cli 0.162.0-alpha.17.2. They are observations of earlier skill revisions, not certification of the current checkout. Actual inputs, outputs, and available manifests remain in the result directories below.

Historical transcripts and manifests preserve their original names, languages, and snapshot paths as evidence; they are not current instructions or live file references. Current guidance and scenarios use English and the ABC name. Do not rewrite historical observations to imply that the renamed skill or translated fixtures were tested by those runs.

| Evidence | Interpretation |
| --- | --- |
| [Initial behavioral probes](results/behavioral-quality) | Shared-mechanism reasoning, justified separation, existing-capability reuse, traceability, structural fixes, and direct help were observed. The Product Owner case repeatedly promoted purchase reversibility from a capability into a required invariant; the sound-design conclusion also added unnecessary conditions. |
| [Capability-to-requirement tests](results/capability-requirement) | The original capability promotion did not recur in either fresh Product Owner case. Opening-first interaction asked about the business problem, but combined-context completion still recommended before clarifying it. The reporting case incorrectly classified a delivery target as an invariant. These remain partial failures, not an all-pass result. |
| [Automation economics tests](results/automation-economics) | Five synthetic cases supported controlled manual work, justified automation, business adaptation, rejection of harmful standardization, and existing configuration. Cross-team benefits and burdens were distinguished without invented monetary ROI. The Product Owner regression still clarified the business problem late and had not converged after two turns. |
| [ABC decision-stability test](results/decision-stability) | A fresh four-turn session retained the scheduler recommendation through both pressure-only challenges, then revised toward the existing isolated runner when the security premise changed. The response attributed unverified implementation correctly. The direct-question regression returned only dictionary.get. However, the final invariant section omitted some required Scope/Verification/Enforcement/Failure impact detail, so only the stability and direct-help criteria are supported, not an all-pass completion result. |

The initial probes supplied opening and clarification together. Later runs included two-turn conversations, but many cases remained single-turn completions. All references were injected, so those runs do not establish progressive disclosure, automatic activation, or natural reference co-loading. Model identity was not captured in every run, grading was performed by the implementing agent, and there is no matched pre-change multi-turn baseline or calibrated aggregate pass rate. Some original outputs contain encoding artifacts; preserve them as recorded evidence.

Prior format validation and CLI discovery succeeded; neither proves behavior in Copilot or another client. End-to-end client invocation, installation/update behavior, cross-client equivalence, broader language coverage, and repeated real-world conversations remain unverified. The rubric thresholds are proposed gates requiring calibration. Test these gaps when relevant rather than treating historical successful process exits or static instruction review as behavioral passes.

The ABC stability run used codex-cli 0.162.0-alpha.17.2 on 2026-10-16 with the runtime default model (identity not independently captured). Only SKILL.md was supplied initially, with optional references available read-only; no reference was read in either case. Future turns and evaluation criteria were withheld. Both fresh sessions completed successfully, totaling five agent turns. This is one author-reviewed run, not repeated cross-model evidence. The manifest records the tested file hashes. Renaming, language, and link checks passed alongside both skill format validators; historical transcript content was not translated or relabeled.
