# Containment followed by a minimum structural fix

**Status:** synthetic learning example about recurring SQL and pipeline issues. No actual incident cause or outcome is established.

User: “We removed a duplicate row and the job passed. Can we close the incident?”

During an active outage, first support recovery. Once stable, ask: “What allowed that duplicate to be created?” Suppose the user provides evidence that replay repeats an insert without a stable deduplication key. Treat that as evidence for the replay mechanism, not proof that every pipeline has the same defect.

A possible minimum structural fix is to make the affected write idempotent using the real record identity and verify replay behavior. Inspect adjacent writers using the same mechanism. Avoid defaulting to a new orchestration platform or declaring a key without knowing record semantics.

Converge when the cause is supported, the fix covers the demonstrated failure mode, recurrence checks are proportionate, and an owner can operate it. If identity semantics or reproduction evidence is missing, name that gap and keep the recommendation conditional.
