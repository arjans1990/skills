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

## Choose the boundary and response

When relevant, state a condition with its scope, justification, validation or enforcement point, and violation response. This is a reasoning aid, not a required output template or questionnaire. Ask the most consequential unresolved question first. Consider changes that could invalidate it, including changes after a deployment check has passed.

Prefer making conditions executable where practical, using existing constraints, referential checks, schema or contract validation, tests, CI/deployment checks, infrastructure policy validation, or runtime assertions. Monitoring and reconciliation may be appropriate when prevention cannot cover external changes. Avoid checks at every layer unless distinct failure paths justify them. A documented review with a clear owner may suffice for infrequent, low-risk changes; acknowledge what it cannot guarantee.

Choose what happens on violation: for example, reject invalid activation, quarantine an invalid record, fail a contract check, or alert and reconcile drift. The response must fit the risk and availability needs; never prescribe universal fail-closed behavior. A dedicated rules engine or governance platform is not warranted merely because a few conditions exist.

## Small illustrations

All examples are synthetic and conditional on the stated architecture, not universal requirements.

- **References:** for an activated mapping, each canonical attribute has a definition and each source reference resolves under the declared mapping rules. DATA_SOURCE = ERP may resolve directly to a staging object or through an explicit registry. The invariant is valid resolution with the defined meaning, not equal physical names. See the linked traceable-relationships example from SKILL.md for provenance reasoning.
- **Contracts:** a published version-2 event must satisfy its declared required fields, and consumers must be compatible with the version they use. A producer contract test or publication check may be sufficient; do not introduce an event platform just for validation.
- **Deployment:** if production resources must have owners and required security controls, verify these against actual deployed state at the appropriate boundary. A clean configuration file alone cannot establish that subsequent drift is absent.
- **Agents:** a tool call must satisfy the tool's input contract; a verification claim must be supported by evidence actually retrieved; sensitive information must remain within the applicable authorized boundary. Configuration alone is not evidence that a runtime action complied.

For an incident, first support recovery. Then identify a violated condition or missing constraint, why it was possible, and the smallest structural fix covering the demonstrated recurrence path. If the condition or evidence is unknown, keep the diagnosis conditional. Stop when the important conditions are justified and the checks and residual risk are proportionate.
