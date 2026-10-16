# Decisions and missing evidence

## MVP defaults

- One skill with progressive domain references; no required custom agent or dependent skill.
- Automatic discovery plus explicit invocation, using only standard frontmatter fields. This is a reversible default, not evidence that the original discussion settled invocation policy.
- Constructive, rigorous tone; one substantive question per turn; bounded relevant inspection.
- Short recommendations where useful; ADRs only on request or for material decisions needing a record.
- Keep existing MIT licensing. No substantial upstream text was copied, so no upstream grilling dependency or license compatibility claim is made.

## Unresolved

- Historical transcripts, final schemas, migration decisions, measured outcomes, and detailed domain preferences are unavailable. The principles are not independently verified personal quotations or preferences. Do not strengthen those claims.
- Authorization to publish additional real case details has not been supplied. Bundled examples use only generalized architectural lessons or explicitly synthetic material. Further cases need evidence and publication review.
- End-to-end Copilot and other-client behavior needs testing in the actual supported clients. A valid directory and CLI discovery do not establish quality or cross-client equivalence.
- Behavioral evaluation thresholds are proposed MVP gates. They need calibration against real conversations, including Dutch conversations and justified exceptions.
- The upstream grilling repositories and licenses have not been audited because no material was reused. Review both before any future copying.
- A separate VS Code agent persona remains a possible later feature, with no MVP dependency.

The repository remote provides the installation source arjans1990/skills. Availability of these local additions on GitHub depends on a separate push/publication step.
