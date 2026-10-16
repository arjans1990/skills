# Architectural invariants

An architectural invariant is a condition that must remain true for correctness within an explicit scope, despite changes to implementation, configuration, or technology. Scope may be a contract version, environment, lifecycle stage, or business context. Select the few conditions consequential to the current decision; do not derive an exhaustive rule catalog.

Traceability establishes where relationships lead. Semantic integrity establishes whether their meanings agree. Invariants define what must remain true. Validation establishes whether those conditions hold for the evidence checked; enforcement prevents or responds to violations. A test passing once is not proof that a condition always holds at runtime.

## Distinguish the condition from its inputs

| Kind | Example | Architectural treatment |
| --- | --- | --- |
| Invariant | Every production destination resolves to an authorized endpoint at activation. | Establish scope, evidence, enforcement boundary, and violation response. |
| Configuration | Which endpoint a deployment selects. | Allow intended variation while preserving the scoped condition. |
| Policy | Which destinations are authorized under the current policy version. | Permit deliberate policy evolution; validate against the applicable version. |
| Assumption | The endpoint never disappears after activation. | Seek evidence or design for failure; do not silently promote it to an invariant. |
| Operational target | Deliver 99% of requests within a stated latency. | Treat as a measured target, not a guarantee that every request is fast. |

A business rule can constrain correctness in an explicit context, but not every business rule is architectural or permanent. For example, a current discount percentage is policy; applying the approved policy version consistently may be an invariant. Ask what justifies a proposed condition before enforcing it.

“Can” does not establish “must”: if a user says purchases can be reversed, that is a capability, not a requirement to preserve reversibility. Versioning likewise does not establish an agreed mapping-activation invariant. Before reporting an established invariant, trace its necessity to an actual requirement or explain why violating it would contradict a justified correctness condition. A possible loss of a feature is not itself that justification. If necessity is unknown, omit the candidate or label it as a proposed constraint requiring confirmation; marking it “Unverified” does not cure an unjustified requirement.

## Choose the boundary and response

During grilling, identify candidate conditions and challenge why correctness requires them. Ask the most consequential unresolved question first. Consider changes that could invalidate a condition, including changes after a deployment check has passed. Do not treat the completion fields below as an interview checklist.

Prefer making conditions executable where practical, using existing constraints, referential checks, schema or contract validation, tests, CI/deployment checks, infrastructure policy validation, or runtime assertions. Monitoring and reconciliation may be appropriate when prevention cannot cover external changes. Avoid checks at every layer unless distinct failure paths justify them. A documented review with a clear owner may suffice for infrequent, low-risk changes; acknowledge what it cannot guarantee.

Choose what happens on violation: for example, reject invalid activation, quarantine an invalid record, fail a contract check, or alert and reconcile drift. The response must fit the risk and availability needs; never prescribe universal fail-closed behavior. A dedicated rules engine or governance platform is not warranted merely because a few conditions exist.

## Make significant conclusions explicit

When a relevant review reveals important invariants and enough information exists to formulate them, include a section titled **Architectural Invariants**. Prefer 2–5 meaningful conditions, but include only one if that is all the decision needs. Omit the section when it adds no value. This is conditional completion behavior, not a mandatory report for every conversation or an automatic ADR.

For each significant invariant, provide these fields in a compact table or short labeled block:

| Field | Content |
| --- | --- |
| Invariant | Precise, testable statement of what must remain true; distinguish an established condition from a proposed constraint or unresolved assumption. |
| Scope | Applicable environment, version, lifecycle stage, or other conditions. |
| Verification | How compliance can be demonstrated; separate available evidence from a recommended check and state its coverage. |
| Enforcement | Existing prevention or detection mechanism and its boundary/limitations, or an explicit gap and proposed mechanism. |
| Failure impact | Concrete consequence of violation, explaining why the condition matters. |

Keep verification and enforcement separate, not a single mutually exclusive status:

- **Verification: Verified** when available evidence demonstrates current compliance within the stated coverage; **Unverified** when it has not been checked; **Violated** when evidence shows noncompliance. Qualify sampled, historical, or partial checks rather than generalizing them to all records or future behavior.
- **Enforcement: Enforced** only when evidence supports an existing prevention or detection mechanism. Name its limitations. Otherwise state **not evidenced**, **missing**, or **proposed**, as appropriate. Documentation of an intended control alone proves neither compliance nor enforcement.

An invariant can currently be verified without enforcement. A deployed enforcement mechanism may cover new writes while historical records remain unverified or violated. Do not collapse these dimensions or invent evidence to fill the fields. If information is missing, name the gap and make the verification or enforcement recommendation conditional.

Before proposing any new check, assess existing database constraints, type systems, contract tests, deployment mechanisms, or other safeguards. Recognize sufficient guarantees within their actual scope; do not automatically create validation code or duplicate controls for every invariant.

**Synthetic concise output example:**

**Architectural Invariants**

- **Invariant:** Every active datasource identifier resolves to a valid source under the declared mapping rules.
- **Scope:** All active datasource configurations.
- **Verification:** Unverified; compare identifiers with the authoritative registry or actual source objects. No inspection results were supplied.
- **Enforcement:** Not evidenced; reuse existing configuration validation if it checks resolution, otherwise propose a lightweight activation or CI check.
- **Failure impact:** Broken ingestion, missing data, or incorrect lineage.

## Small illustrations

All examples are synthetic and conditional on the stated architecture, not universal requirements.

- **References:** for an activated mapping, each canonical attribute has a definition and each source reference resolves under the declared mapping rules. DATA_SOURCE = ERP may resolve directly to a staging object or through an explicit registry. The invariant is valid resolution with the defined meaning, not equal physical names. See the linked traceable-relationships example from SKILL.md for provenance reasoning.
- **Contracts:** a published version-2 event must satisfy its declared required fields, and consumers must be compatible with the version they use. A producer contract test or publication check may be sufficient; do not introduce an event platform just for validation.
- **Deployment:** if production resources must have owners and required security controls, verify these against actual deployed state at the appropriate boundary. A clean configuration file alone cannot establish that subsequent drift is absent.
- **Agents:** a tool call must satisfy the tool's input contract; a verification claim must be supported by evidence actually retrieved; sensitive information must remain within the applicable authorized boundary. Configuration alone is not evidence that a runtime action complied.

For an incident, first support recovery. Then identify a violated condition or missing constraint, why it was possible, and the smallest structural fix covering the demonstrated recurrence path. If the condition or evidence is unknown, keep the diagnosis conditional. Stop when the important conditions are justified and the checks and residual risk are proportionate.
