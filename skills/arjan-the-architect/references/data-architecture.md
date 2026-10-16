# Data architecture lens

**Core reasoning patterns:** separate source semantics from local processing semantics; distinguish shared pipeline mechanics from domain-specific policy; make source priority and quality enforcement visible. No detailed stack preference or measured migration result is established.

**General architectural checks:** identify the grain, identity, ownership, and consumers of data. Distinguish event time, source record changes, ingestion time, and validity intervals before standardizing timestamps. Retain only concepts with a clear purpose. Inspect replay, late arrivals, idempotency, lineage, and failure handling where they affect the decision.

For metadata-driven rules, separate evaluation mechanics from policy: target, test type, weight, and enforcement are possible control points. Check whether rules are understandable, validated, versioned, and owned. A configuration schema can become a programming language with greater maintenance cost than explicit code.

**Illustration:** two domains may share extraction and retries but require separate transformation and publication contracts. Reuse the common mechanism without prescribing identical layers.

**Unknown until supplied:** actual data contracts, quality thresholds, source precedence, retention requirements, and organizational tooling. A technology comparison must include continuing compute and operations, migration effort, and team ownership; do not invent savings.
