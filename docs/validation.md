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

This is an author review of instructions, not an independent behavioral evaluation. The fifteen scenario fixtures and rubric are ready for use; no model conversation scores or pass rate are claimed. Copilot UI invocation, actual installation/update behavior, other clients, and remote availability have not been tested. No personal agent configuration was changed and no files were pushed.

## Reproduce

Run the README validation command and CLI discovery command from the repository root. Check Markdown relative links with a local link checker, excluding external URLs and anchors. Execute evaluations/scenarios.md in fresh target-client sessions using evaluations/README.md before calling the behavior validated.

## Relationship-integrity revision

Added a distinct principle and reasoning move for end-to-end traceability, semantic consistency, and implementation integrity. Domain lenses cover provenance and enforcement, contracts and consumers, desired versus deployed state, effective permissions, and AI evidence and capabilities. The synthetic DATA_SOURCE example permits explicit mappings with different physical names and distinguishes a valid reference from correct meaning.

After this revision, both format validators passed again, local Markdown link targets resolved, and `git diff --check` reported no whitespace errors. Scenarios 11–15 and the relationship-integrity rubric dimension are new fixtures, not executed behavioral results. They cover nonexistent handlers, conflicting identifier semantics, runtime provenance mismatches, inherited-permission drift, and proportionate existing validation when implementation evidence is unavailable. The skill still uses standard frontmatter and requires no new runtime dependency.
