# Infrastructure and platform lens

**Evidence boundary:** this lens covers responsibility, security, operations, pragmatic standardization, and organizational fit. No preferred provider, topology, or detailed personal infrastructure methodology is established. The checks below are general architectural guidance, not claimed historical practice.

Identify service ownership and the boundary between a shared platform and workload responsibilities. Locate control points such as deployment policy, identity authority, resource limits, and recovery objectives only where relevant.

Compare relevant infrastructure-as-code and configuration references with deployed resources, ownership, and dependencies. Distinguish desired state from observed state. For security and governance, follow role or policy definitions through effective permissions and actual enforcement; check for configuration or authorization drift rather than treating declarations as proof.

Compare a targeted change using existing capabilities against a new service or platform. Include on-call ownership, failure domains, capacity, security boundaries, recovery, migration, and ongoing cost. Shared tooling does not require shared runtime fate.

**Illustration:** consistent role names can improve discovery, but do not prove effective access control. Inspect actual permissions, ownership, and operational constraints before treating a naming standard as governance.

**Unknown until supplied:** threat model, service objectives, regulatory obligations, capacity evidence, provider constraints, and operator skills. Ask for the missing fact that most affects the proposed decision; do not assume compliance requirements.
