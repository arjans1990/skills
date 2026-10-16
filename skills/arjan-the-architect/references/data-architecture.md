# Data architecture lens

**Core reasoning patterns:** separate source semantics from local processing semantics; distinguish shared pipeline mechanics from domain-specific policy; make source priority and quality enforcement visible. No detailed stack preference or measured migration result is established.

**General architectural checks:** identify the grain, identity, ownership, and consumers of data. Distinguish event time, source record changes, ingestion time, and validity intervals before standardizing timestamps. Retain only concepts with a clear purpose. Inspect replay, late arrivals, idempotency, lineage, and failure handling where they affect the decision.

For metadata-driven rules, separate evaluation mechanics from policy: target, test type, weight, and enforcement are possible control points. Check whether rules are understandable, validated, versioned, and owned. A configuration schema can become a programming language with greater maintenance cost than explicit code.

Trace a relevant canonical attribute through source-to-target mappings, actual objects and values, transformations, and consumer interpretations. A valid object reference does not prove consistent business meaning or source provenance. Verify that configured quality rules are actually enforced, and check affected mappings and consumers when definitions change.

**Illustration:** two domains may share extraction and retries but require separate transformation and publication contracts. Reuse the common mechanism without prescribing identical layers.

**Unknown until supplied:** actual data contracts, quality thresholds, source precedence, retention requirements, and organizational tooling. A technology comparison must include continuing compute and operations, migration effort, and team ownership; do not invent savings.

## Illustration: timestamp semantics before standardization

**Status:** generalized architectural example; not a verified case study. No transcript, final schema, implementation, or measured outcome is available.

The initial discussion sought a broad timestamp standard. It distinguished source-system perspective from local-record perspective, then reduced overlapping or low-value concepts.

**Illustrative exchange, not a transcript:**

- User: “Every table should have created, updated, loaded, processed, and validity timestamps.”
- Agent: “Some may describe the source record and others our local processing. Which consumer decision requires distinguishing those times?”
- User: “Consumers need source change time; operators need ingestion time. We do not model business validity.”
- Agent: “Those two semantics justify two fields for this scope. Leave validity out until a real consumer needs it; document what each retained timestamp means.”

The lesson is to explore broadly and retain the smallest coherent model, not to prescribe two fields universally. Missing facts include deletion semantics, replay behavior, timezone conventions, and downstream needs; investigate them only if they affect the current decision.
