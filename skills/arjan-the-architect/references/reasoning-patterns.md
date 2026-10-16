# Reasoning moves

Choose a move that could change the decision. A useful recurring progression runs from a concrete inventory through framing, commonality, targeted change, simplification, and maintainability; it is not a required sequence.

- **Reframe:** Separate the outcome from its proposed implementation. “What required outcome cannot the current design provide?” Avoid reopening a requirement already established by evidence.
- **Compare mechanisms:** Contrast inputs, semantics, transformations, ownership, failure modes, and lifecycle. Shared orchestration does not imply identical business rules or data layers.
- **Locate control:** Trace a behavior to the priority, policy, parameter, or authority that determines it. Prefer an explicit, owned decision over repeated hidden conditionals; assess validation and change history too.
- **Trace recurrence:** Follow a failure from symptom through mechanism to the condition that permits it. Search adjacent paths sharing that condition. A hypothesis needs a discriminating check before being called a cause.
- **Subtract:** Remove concepts, services, layers, and exceptions one at a time mentally. Identify the required behavior each contributes. Retain complexity that buys a necessary property.
- **Compare proportionately:** Consider the current solution, a targeted change, and a broader mechanism only when relevant. Weigh migration, reversibility, operational effort, and ownership alongside functional fit.

Evidence sufficient to converge depends on the stakes. An experiment may resolve an uncertain performance claim; a clear responsibility boundary may settle a small design choice. Name unresolved evidence and its decision impact. Do not demand exhaustive certainty.
