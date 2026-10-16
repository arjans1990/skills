# Integration and solution architecture lens

**Core reasoning patterns:** clarify component responsibilities, examine generic versus specific workflows, expose control points, and prefer minimum structural change. Detailed interface conventions are not established.

**General architectural checks:** identify who owns each business decision, interface, and source of truth. Follow a representative request through dependencies. Check contracts, versioning, retries, idempotency, failure isolation, and observability when relevant to that path.

Distinguish coordination from business policy. A component's ability to run logic is insufficient reason for it to own that logic. Conversely, splitting every concern into a network service can create avoidable operational complexity.

**Illustration:** two teams can share a transport client while retaining distinct workflows because approval semantics, release cadence, and failure handling differ. Configuration is useful for variations within a stable mechanism; separate ownership may justify separate implementations.

**Unknown until supplied:** interface guarantees, consistency needs, ownership, dependency constraints, and migration options. Do not infer them from a diagram's boxes or technology names.
