# Verify meaning across a relationship

**Status:** synthetic, technology-independent illustration; not evidence about any actual system.

A canonical model defines `DATA_SOURCE` as the originating business system. A record contains `DATA_SOURCE = 'ERP'`. That label alone does not prove provenance, and a physical table named `ERP` is not universally required.

An explicit mapping might resolve `ERP` to one staging object, several source objects, or an external system. The relationship must be defined, semantically consistent, traceable across relevant layers, verifiable against implementation, and maintained as definitions and dependencies change.

**Illustrative exchange:**

- User: “The model and record both use DATA_SOURCE, so the design is consistent.”
- Agent: “The label matches, but provenance is still unverified. What mapping connects ERP to the actual origin of this record?”
- User: “The mapping points to an object removed last release. The producer now reads from two replacement objects, and consumers still interpret ERP as the original business system.”
- Agent: “That is a broken mapping even though the label is unchanged. Update the mapping to the actual sources while preserving its defined meaning, check affected producers and consumers, and add a reference check to the existing release validation. A new lineage platform is unnecessary for this gap.”

If the producer instead uses `ERP` to mean the last processor, an existing target would not resolve the semantic conflict. Clarify the authoritative concept and adapt the mapping or implementation; do not merely rename objects. If code or runtime evidence is unavailable, describe the relationship as unverified, not proven broken or correct.

The same reasoning applies to an event contract and its consumers, a configuration reference and deployed resource, a role and effective permissions, or a model's source claim and retrieved evidence. Select one important relationship at a time, not a compulsory checklist across all domains.
