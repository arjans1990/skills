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

## Capability-to-requirement investigation

### Evidence and likely contributors

The earlier Product Owner output explicitly called purchase reversibility “Required by your clarification,” although the fixture said only “can be reversed.” This was a necessity error, not a missing compliance check: marking the invented requirement Unverified would still be wrong. The main recommendation could be reasonable while the invariant table silently expanded the business requirements.

Two plausible contributors are the completion emphasis on explicit invariants (with a preferred count) and insufficient separation of business needs from features during initial framing. The previous combined-context tests could not evaluate whether the agent challenged the problem framing before selecting a solution. These are hypotheses supported by output patterns, not a proven account of model internals. The last concrete “can is not must” clarification from the previous revision was also untested, so this run cannot isolate the effect of the latest edits from that earlier change.

### Small targeted correction

Replaced the existing framing bullet and Reframe move to distinguish business outcomes/actual requirements, existing capabilities/technical possibilities, assumptions/proposals, and justified architectural constraints/invariants. When the business problem is unclear, question that framing before recommending a solution; do not reopen requirements already established. Strengthened the existing invariant admission rule: necessity must trace to an actual requirement or a correctness argument, and possible feature loss alone is not that argument. No new principle, reference, checklist, or runtime dependency was added.

Scenario 25 now explicitly tests framing and requirement origin; scenario 26 checks transfer to an unrelated reporting capability. Existing scenarios provide regressions. Success requires more than the absence of the word “reversible”: inspect the meaning of each recommendation and invariant for invented obligations, while preserving explicit constraints.

### Protocol and actual results

2026-10-16, codex-cli 0.162.0-alpha.17.2. Eight fresh sessions, ten agent turns, all execution exits 0. Two sessions were resumed once with their fixture follow-up, so they tested actual conversation history. Other completion cases supplied opening and clarification together; case 7 supplied only its narrow opening. Each invocation received the skill and all reference files, without evaluator criteria, with tools prohibited in the prompt and a read-only sandbox. No model override was used; the model identity was not independently captured in this run's result files.

Inputs and outputs are in [the result directory](../evaluations/results/capability-requirement); its manifest records runtime, context hash, files, base commit, and protocol. Scores below are author assessments of observed outputs, not independent automated grading. No output was rewritten, and no failed case was silently discarded.

| Fresh case | Observable criteria and actual evidence | Result |
| --- | --- | --- |
| 25, conversation | First question asks for an example of a change repeated across departments, before a firm recommendation. On clarification, explicitly says reversibility “is a capability; it does not by itself establish a requirement.” Reports only independent authorization/ownership as an invariant, with implementation unverified. Uses plain language and no invented savings. | Supported: framing, requirement origin, explicit-constraint preservation, and convergence in this run. |
| 25, combined completion | Explicitly rejects reversibility as a requirement and reports only the supplied authorization condition. However, recommends the shared presentation/separate decisions solution before asking which expensive changes remain duplicated. | Capability failure absent; framing-order criterion only partially satisfied. The recommendation is evidence-qualified, but does not first establish the business change problem. |
| 26, conversation | First response rejects universal minute refresh as a capability-derived invariant and asks which business decision needs it. After clarification, accepts the existing daily job with no new infrastructure. However, places the daily 08:00 delivery requirement in Architectural Invariants, despite the fixture requiring operational-target treatment. | Partial: transfer of capability distinction and framing supported; operational-target versus invariant classification fails. It qualifies evidence as limited to observed runs, so it does not claim a future guarantee. |
| 3, completion | Reuses the existing scheduler; names unmet isolation/lifecycle requirements as reversal evidence. No new service or invented obligations from feature availability. | Supported regression. |
| 6, completion | Accepts the sound design, adds no new validation mechanism, and asks no questions. Its conditions concern duplicate effects and authorized access, rather than the previously inferred mapping-activation condition. | Supported convergence regression; invariant output remains somewhat verbose. |
| 7, direct opening | Returns only the dictionary.get expression, with no review or invariant section. | Supported direct-help regression. |
| 18, completion | Rejects 10% as permanent architecture; preserves the explicit requirement to record the applied approved campaign version. Separates configuration review from enforcement of the order-version relationship. | Supported policy/constraint regression. |
| 22, completion | Preserves the required account reference invariant, marks current compliance Violated and new-write enforcement active, and recommends existing database validation rather than a service. | Supported enforced-invariant regression. |

### Conclusion and remaining limits

The original Product Owner capability-to-requirement failure did not recur in either fresh case. This is evidence of the observed runs, not proof that the skill can never make the error. A framing-order weakness persists in combined-context completion, and the transfer case still overclassifies a delivery target as an invariant. These are explicit partial failures; the suite is not all-pass. No further guidance was added merely to chase this run's wording.

The opening-first Product Owner conversation demonstrates a concrete improvement over the earlier untested framing behavior, but there is no matched pre-change multi-turn baseline. All references were injected, so progressive loading and discovery were not tested. Only two conversations had multiple turns, one default runtime configuration was used, and scoring was performed by the implementing agent. More repeated and audience-varied conversations are needed before claiming reliable generalization. Existing principles and constraints remain intact; recognition of available capabilities must not erase genuine requirements.
