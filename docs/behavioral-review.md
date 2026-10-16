# Behavioral quality review

## Assessment and priorities

The existing skill has strong scope control, evidence boundaries, invariant semantics, and explicit convergence. Its overlapping traceability, invariant, and interaction guidance already covers structural correctness; another principle or reference would add little. The weak points were application: prioritizing a tension, offering an actual alternative rather than only asking for simplicity, specifying reversal evidence, and explaining the same judgment to different audiences.

Prioritized changes:

1. Spend the next question on the tension most likely to change the decision, rather than reviewing every dimension.
2. Compare a concrete existing-capability alternative with the proposal, preserving essential guarantees and stating sacrifices.
3. Trace upstream origins and downstream consumers, separating documented, inspected, assumed, and broken links.
4. Make consequential recommendations revisable through evidence and the smallest useful check, without requiring experiments when facts suffice.
5. Adapt vocabulary to the audience and converge when justified.

These refine SKILL.md, reasoning-patterns.md, and interaction-style.md without adding principles, dependencies, or runtime files. Existing scenarios 1 and 3 gained decision-quality criteria; 24 and 25 add the missing canonical-change and Product Owner coverage. The evaluation guide adds decision-quality and audience-fit dimensions and identifies the eight-case review set.

## Executed completion probes

Date: 2026-10-16. Runtime: codex-cli 0.162.0-alpha.17.2, configured model gpt-6.1-sol, low reasoning. Eight fresh ephemeral read-only executions completed with exit 0. Instructions included SKILL.md and all domain/reference files, but no rubric or expected answers. Each case supplied both its opening and clarification in one turn. Outputs are preserved in evaluations/results/behavioral-quality/.

This tests conclusions under supplied context, not progressive reference selection, automatic activation, first-question choice, or multi-turn listening. Results below are author judgments against the observable criteria, not independent rubric scores or a benchmark pass rate. There was no pre-change runtime baseline.

| Scenario | Observed evidence | Assessment |
| --- | --- | --- |
| 1: Shared pipelines | Recommended shared mechanics with explicit domain configuration; retained separate executions and named isolation/semantic differences as reversal conditions. | Supported completion criteria. The bounded representative checks were concrete; first-question behavior untested. |
| 9: Separate workflows | Kept workflows separate, recognized existing transport reuse, and cited independent ownership, releases, and failure isolation. | Supported separation and convergence; no forced engine. |
| 3: Existing scheduler | Recommended the existing scheduler, identified operational burden and missing new-service ownership, and named unmet requirements as reversal evidence. | Supported reuse and conditional judgment; did not invent costs. |
| 24: Canonical change | Followed source mapping through billing transformation/API, preserved account-holder meaning, proposed additive recipient identity, and left diagram-only analytics usage unknown. | Supported bidirectional traceability, concrete alternative, and bounded contract checks. No runtime verification claimed. |
| 17: Recurring incident | Identified concurrent check-then-insert race; proposed shared-store uniqueness and compatible retry handling, with concurrency reproduction. | Supported structural fix; explicitly avoided claiming exactly-once payment effects. |
| 25: Product Owner | Explained separate approval decisions and shared screens in plain language, preserving independent authorization. However, promoted reversible purchases into a required invariant. | Partial: useful judgment and audience fit, but an inferred obligation. Triggered a narrow correction and rerun. |
| 6: Sound architecture | Accepted the job, identified the scheduler dependency, and stopped asking questions. Added an unverified mapping-selection invariant/check. | Supported basic convergence; completion was heavier than necessary. Included in targeted rerun. |
| 7: Narrow Python | Returned only dictionary.get with a missing-key default. | Supported direct help; no interview or invariant section. |

## Observed correction and limits

The first run exposed promotion of a described capability into a requirement and excessive completion detail. Interaction guidance now explicitly forbids inferred obligations, promised savings, and reopening settled questions without decision impact. Only the two affected cases were rerun; their outputs are retained alongside the original attempts. A rerun is evidence about those cases, not proof of reliable behavior across models or sessions.

Both reruns exited 0 and retained the main architectural recommendation. Scenario 25 still called purchase reversibility required, despite the added interaction instruction; scenario 6 still included the mapping-selection condition. The correction did not resolve those completion weaknesses in these probes. A final, more concrete clarification was therefore placed at invariant selection itself: “can” is not “must,” with both examples. That final clarification has passed static validation but has not had another runtime probe. Scenario 25 remains partial and the invariants-output behavior needs further multi-turn evaluation rather than a claim of success.

The expected before/after difference is fewer unfocused questions and more concrete, evidence-qualified recommendations. Only the post-change completion probes were executed, so comparative improvement and multi-turn behavior remain unverified. Client integration and automatic skill selection also remain untested. Unicode replacement characters occurred in some CLI output; preserved transcripts retain those artifacts rather than reconstructing wording.
