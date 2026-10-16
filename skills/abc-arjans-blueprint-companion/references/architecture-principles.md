# Principles and their limits

These define the skill's architectural reasoning principles. Apply the ones that matter to the decision, not every principle as a questionnaire.

| Principle | Architectural use | Guard against |
| --- | --- | --- |
| Pattern recognition | Compare mechanisms across systems, processes, and incidents; test meaningful differences. | Treating superficial resemblance as equivalence. |
| Root-cause thinking | Mitigate incidents, then identify recurrence and other affected paths. | Delaying recovery for a complete explanation. |
| Abstraction through simplification | Explore concepts, find common structure, then remove overlap. | Building a framework merely to unify names. |
| Separation of concerns | Make responsibility and ownership boundaries explicit. | Putting logic somewhere only because it can execute it. |
| Configuration over duplication | Represent genuine variations as explicit rules, metadata, or configuration. | Forcing distinct processes into one engine. |
| Control points | Expose the few policies, priorities, or parameters that govern behavior. | Making every implementation detail configurable. |
| Minimum effective change | Change the smallest relevant area that addresses the structural cause. | Mistaking a repeated patch for a structural fix, or defaulting to a rewrite. |
| Transparency by design | Make business rules, dependencies, and behavior discoverable. | Hiding complexity inside metadata or scattered exceptions. |
| End-to-end traceability, semantic consistency, and implementation integrity | Make important relationships between definitions, canonical concepts, configuration, implementation, runtime behavior, and consumers explicit, meaningful, verifiable, and maintained through change. | Mistaking matching names or correct individual components for correct relationships; requiring a registry or lineage platform for every link. |
| Architectural invariants | Make the few conditions required for correctness explicit within a defined scope; choose how to validate or enforce them and handle violations. | Elevating changeable policy, targets, assumptions, or temporary implementation choices into universal truths; duplicating checks without a reason. |
| Maintainability first | Design for the next operator and engineer after the original architect leaves. | Optimizing only for initial construction. |
| Pragmatic standardization | Standardize shared semantics and allow justified exceptions. | Governance that creates work without improving outcomes. |
| Technology as a means | Use existing capabilities when sufficient; justify new operational cost. | Favoring either novelty or the existing stack regardless of fit. |
| Iterative refinement | Revisit assumptions and remove unnecessary moving parts; own a justified architectural choice within mandate and accept its tradeoffs. | Endless analysis of equivalent alternatives, artificial scoring, or delegating judgment to consensus; confusing architectural responsibility with business authority. |
| Organizational fit | Improve process and design together for sustainable total business/IT value; include skills, migration, beneficiaries, burden owners, and who can authorize, deliver, and sustain each change. | Treating historical processes as immutable or forcing change for technical convenience; assuming willingness, authority, or capacity; mistaking shifted cost for total saving. |
| Intellectual honesty | Expose drawbacks, uncertainty, and ongoing costs of preferred choices. | Unsupported savings, guaranteed outcomes, or vendor advocacy. |
