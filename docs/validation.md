# MVP validation record

Date: 2026-10-16. Scope: local first version, before publication. Results apply to this checkout, not to the version currently on GitHub.

## Executed checks

| Check | Result |
| --- | --- |
| Agent Skills reference validator | `uvx --from skills-ref agentskills validate skills/arjan-the-architect` passed: “Valid skill”. |
| Skill-creator quick validator | `quick_validate.py skills/arjan-the-architect` passed: “Skill is valid!” |
| CLI directory discovery | `npx.cmd --yes skills@latest add . --list` found exactly one skill named arjan-the-architect; exit 0. Listing did not install the skill. |
| Local Markdown links | Checked repository Markdown relative link targets after adding this record; all resolve. |
| Entrypoint size | SKILL.md is below the specification's recommended 500-line limit. |

The specification's example command `skills-ref validate` could not run: the resolved PyPI package exports `agentskills`, not `skills-ref`. Retrying with the exported executable passed. README records the working command rather than silently repeating the documentation mismatch.

## Static content review

The architectural principles are retained with counterweights in architecture-principles.md. The entrypoint links every domain reference and example, keeps runtime context separate, requires one substantive question at a time, and includes direct-help and convergence exits. Examples distinguish generalized lessons from synthetic dialogue and do not claim measured historical results. The existing LICENSE is preserved.

This is an author review of instructions, not an independent behavioral evaluation. The thirty-one scenario fixtures and rubric are ready for use; no model conversation scores or pass rate are claimed. Copilot UI invocation, actual installation/update behavior, other clients, and remote availability have not been tested. No personal agent configuration was changed and no files were pushed.

## Reproduce

Run the README validation command and CLI discovery command from the repository root. Check Markdown relative links with a local link checker, excluding external URLs and anchors. Execute evaluations/scenarios.md in fresh target-client sessions using evaluations/README.md before calling the behavior validated.

## Relationship-integrity revision

Added a distinct principle and reasoning move for end-to-end traceability, semantic consistency, and implementation integrity. Domain lenses cover provenance and enforcement, contracts and consumers, desired versus deployed state, effective permissions, and AI evidence and capabilities. The synthetic DATA_SOURCE example permits explicit mappings with different physical names and distinguishes a valid reference from correct meaning.

After this revision, both format validators passed again, local Markdown link targets resolved, and `git diff --check` reported no whitespace errors. Scenarios 11–15 and the relationship-integrity rubric dimension are new fixtures, not executed behavioral results. They cover nonexistent handlers, conflicting identifier semantics, runtime provenance mismatches, inherited-permission drift, and proportionate existing validation when implementation evidence is unavailable. The skill still uses standard frontmatter and requires no new runtime dependency.

## Architectural-invariants revision

Added a core principle, reasoning move, and progressively loaded reference distinguishing scoped correctness conditions from configuration, evolving policy, unverified assumptions, and operational targets. The reference separates traceability, semantics, invariants, and validation/enforcement, with synthetic cross-domain examples and proportionate violation responses. It permits manual checks where justified and avoids duplicating enforcement without a distinct failure path.

Scenarios 11, 14, and 15 now explicitly assess invariant definition and enforcement boundaries. New scenarios 16–18 assess a broken versioned API contract, a recurring concurrent-write incident caused by a missing constraint, and a campaign rule incorrectly proposed as permanent architecture. The rubric adds scoped invariant reasoning. These are evaluation fixtures, not executed model conversations; no behavioral pass rate is claimed.

Revision checks passed: both skill validators, all 20 local Markdown link targets, and whitespace validation. The entrypoint remains 36 lines with unchanged standard frontmatter and no new runtime dependency. A repository search found no references to the removed project brief or named adopter.

## Signature-question revision

Interaction guidance now includes the Dutch signature challenge and English equivalent, connected to the existing invariant reference. It selects contextual follow-ups, asks only the unresolved part when the full formulation would overload a turn, and skips the challenge for narrow requests or sufficiently justified conditions. The entrypoint's existing interaction link makes this guidance discoverable without duplicating the invariant explanation.

Scenarios 19–20 contrast change-sensitive destination reliability with a direct Markdown syntax request. These are unexecuted behavioral fixtures. Both skill validators and whitespace checks passed; all 21 local documentation link targets resolve, excluding the deliberately synthetic link in scenario 20's expected output. No new runtime dependency or frontmatter field was added.


## Explicit invariant-output revision

Completion guidance now calls for an Architectural Invariants section only when significant conditions add value. The invariant reference defines five concise fields, distinguishes established conditions from assumptions/proposals, and separates verification evidence from enforcement mechanisms and their limitations. Existing sufficient safeguards should be recognized without redundant validation code.

Scenarios 21?23 cover current compliance without enforcement, enforced new writes with violated historical records, and an unsupported performance target versus an unverified correctness condition. Scenario 20 remains the contrasting direct-answer test. These are unexecuted behavioral fixtures; no model-conversation results are claimed.

Both skill validators, all 21 local documentation links (excluding synthetic scenario output), and whitespace checks passed. There are 23 scenario fixtures. No runtime dependencies or frontmatter fields changed.


## Behavioral-quality review

See [the behavioral review](behavioral-review.md) for assessment, prioritized changes, observed outputs, and limitations. Eight single-turn completion probes plus two targeted reruns executed in Codex; transcripts are retained under evaluations/results/behavioral-quality. A Product Owner capability-to-requirement error persisted in the rerun. A final invariant-selection clarification is statically checked but not runtime-tested. No all-pass claim or pre/post comparison is supported. Scenarios now total 25. The reference validator and UTF-8-mode quick validator pass; ordinary Windows quick validation hit a cp1252 decoding error, resolved by `python -X utf8`.


## Capability-to-requirement investigation

See [the updated behavioral review](behavioral-review.md) for causal hypotheses, targeted changes, observable criteria, and actual results. Eight fresh cases (ten turns, including two resumed conversations) completed successfully as runtime executions. Product Owner capability promotion was absent in both reruns; combined-context framing order and the transfer case's operational-target classification remain partial failures. Raw outputs and input turns are preserved in evaluations/results/capability-requirement. These results are not an all-pass claim or proof of reliability. There are 26 scenario fixtures. Both format validators and whitespace checks passed after the guidance changes; documentation links also resolve.


## Automation economics and cross-team burdens

Refined the existing organizational-fit principle, core comparison guidance, reasoning patterns, and interaction style. No new skill, reference, runtime dependency, or financial tooling was introduced. Scenarios 27?31 cover controlled manual execution, justified automation, business adaptation, unacceptable standardization, and lightweight configuration. Seven fresh runtime cases (nine turns) completed with exit 0; actual inputs/outputs and a manifest are under evaluations/results/automation-economics. See the behavioral review for observed successes and limitations, including the still-partial Product Owner framing regression. Both skill validators and whitespace checks passed; local documentation links resolve. The suite now contains 31 scenario fixtures. These results do not establish performance across agents or eliminate previous unresolved failures.
