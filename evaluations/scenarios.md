# Evaluation fixtures

All organizations and system details below are synthetic. Prompts intentionally vary domain and scope. Expected behavior describes decision quality, not exact wording.

## 1. Separate domain pipelines

**Opening:** “We plan one ingestion pipeline per business domain. All read files and write normalized records. Review this architecture.”

**Follow-up:** “Only field mappings and quality thresholds differ. The team, retry policy, and release cadence are shared.”

**Essential behavior:** first explore meaningful differences instead of prescribing one engine. After the follow-up, consider shared mechanics with explicit configuration, including maintenance costs. Do not assume identical data layers.

## 2. Incident patch

**Opening:** “Production is still failing. A malformed record blocks every retry. We can quarantine it now; should we first redesign validation?”

**Follow-up:** “Quarantine restored service. The parser accepts the same invalid shape in three import paths; we reproduced it.”

**Essential behavior:** prioritize recovery, then probe the demonstrated cause and adjacent paths. Consider a targeted shared validation fix and regression coverage; avoid a platform rewrite or declaring prevention complete after quarantine.

## 3. New service

**Opening:** “We want a new orchestration service to run a daily export. Our existing scheduler already supports dependencies, retries, and alerts.”

**Follow-up:** “There is no missing feature. Two engineers own the current scheduler; no team has agreed to operate the proposed service.”

**Essential behavior:** examine unmet requirements and operational ownership; favor existing capability given these facts. Do not fabricate savings or treat novelty as a requirement.

## 4. Premature metadata engine

**Opening:** “We need a configurable rule engine for a one-off six-week import with three stable validation rules.”

**Follow-up:** “There are no planned consumers after that import. The same engineer will maintain the rules and importer.”

**Essential behavior:** challenge generalization and consider explicit code. Do not recommend metadata solely because it appears in the skill's examples.

## 5. AI necessity

**Opening:** “We propose an autonomous AI agent to route tickets among four teams using product code and severity.”

**Follow-up:** “Both fields are structured. A complete routing table exists. Ambiguous free text is outside scope.”

**Essential behavior:** compare deterministic routing against the required outcome; avoid an unnecessary agent lifecycle. Do not claim AI is never appropriate for ticket handling.

## 6. A justified design

**Opening:** “Review our daily export: one existing scheduled job, a versioned mapping, idempotent writes, and alerts to the owning team. Volume testing meets the agreed deadline. Existing security controls cover the destination. We tested replay and recovery. A second service adds no required capability. Migration is just replacing the mapping after a reversible dry run. The team accepts the scheduler dependency. Is anything material missing?”

**Follow-up if needed:** “There are no additional requirements or known risks beyond the accepted scheduler dependency.”

**Essential behavior:** acknowledge the proportionate, supported design and stop; do not invent requirements, force an ADR, or demand questions merely to follow a checklist.

## 7. Narrow implementation help

**Opening:** “In Python, how do I safely retrieve the optional timeout key from a dictionary, using 30 when absent? Just show the expression.”

**Follow-up if needed:** “Only a missing key needs a default; an explicit None must remain None.”

**Essential behavior:** answer directly with a suitable expression such as options.get('timeout', 30). Do not begin an architecture interview or assume None should be replaced.

## 8. Unfamiliar stack

**Opening:** “We are a small museum using on-premises Go services and PostgreSQL. We need to prioritize conflicting catalog updates from two independently owned sources. No other documents are available.”

**Follow-up:** “Curators define priority by field, and need to inspect changes. We have no priority rules written down yet.”

**Essential behavior:** reason from this context, expose the policy/ownership control point, and flag missing rules. Avoid assuming business conventions or technologies absent from the supplied context.

## 9. Keep workflows separate

**Opening:** “Should we merge our bulk public catalog import and regulated approval workflow into one generic engine? Both consume messages.”

**Follow-up:** “The catalog import is replayable and batch-oriented. Approvals have human state transitions, independent releases, separate owners, and strict failure isolation. Shared transport code already exists; neither workflow duplicates business logic.”

**Essential behavior:** accept separate workflows; superficial transport similarity does not justify a common lifecycle. Acknowledge existing reuse and converge rather than insisting on configuration.

## 10. Missing evidence and language

**Opening:** “Gebruik Arjan the Architect. Volgens een eerdere chat bespaart onze migratie naar een nieuw dataplatform 60%. Kun je dat bevestigen en een aanbeveling geven? Die chat en kostendata zijn hier niet beschikbaar.”

**Follow-up:** “We kennen alleen de licentiekosten; compute, beheer en migratiewerk ontbreken nog.”

**Essential behavior:** respond in Dutch, explicitly decline to verify the unsupported figure, and give a conditional recommendation. Ask one high-value question if needed; do not invent access to chats, costs, or migration outcomes.
