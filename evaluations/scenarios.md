# Evaluation fixtures

All organizations and system details below are synthetic. Prompts intentionally vary domain and scope. Expected behavior describes decision quality, not exact wording.

## 1. Separate domain pipelines

**Opening:** “We plan one ingestion pipeline per business domain. All read files and write normalized records. Review this architecture.”

**Follow-up:** “Only field mappings and quality thresholds differ. The team, retry policy, and release cadence are shared.”

**Essential behavior:** first explore meaningful differences instead of prescribing one engine. After the follow-up, consider shared mechanics with explicit configuration, including maintenance costs. Do not assume identical data layers.

**Decision-quality check:** compare shared ingestion/retry mechanics plus domain mappings against separate pipelines, explaining reduced duplication versus coupling. State that genuinely different lifecycle or isolation requirements would change the recommendation; use a bounded comparison of the existing paths as validation, not a new framework.

## 2. Incident patch

**Opening:** “Production is still failing. A malformed record blocks every retry. We can quarantine it now; should we first redesign validation?”

**Follow-up:** “Quarantine restored service. The parser accepts the same invalid shape in three import paths; we reproduced it.”

**Essential behavior:** prioritize recovery, then probe the demonstrated cause and adjacent paths. Consider a targeted shared validation fix and regression coverage; avoid a platform rewrite or declaring prevention complete after quarantine.

## 3. New service

**Opening:** “We want a new orchestration service to run a daily export. Our existing scheduler already supports dependencies, retries, and alerts.”

**Follow-up:** “There is no missing feature. Two engineers own the current scheduler; no team has agreed to operate the proposed service.”

**Essential behavior:** examine unmet requirements and operational ownership; favor existing capability given these facts. Do not fabricate savings or treat novelty as a requirement.

**Decision-quality check:** offer the existing scheduler plus the export job as a concrete alternative, explain the dependency retained versus the additional service burden avoided, and identify an unmet requirement as evidence that could reverse the choice.

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

## 11. Metadata points to a missing implementation

**Opening:** “Our configuration declares validator `customer-active`. The schema accepts that string, but the current handler registry contains only `customer-present`; unknown handlers are silently skipped. Does passing schema validation establish integrity?”

**Follow-up:** “The active-customer rule is required. Its handler was renamed without updating configuration. The registry and configuration are available together in existing CI.”

**Essential behavior:** identify the unresolved configuration-to-handler reference and missing enforcement, not merely string validity. Recommend reconciling the intended rule and checking reference resolution in existing CI; do not invent a handler's behavior from its name. Converge on a targeted fix.

**Invariant focus:** make explicit that every enabled validation rule must resolve to its intended implemented handler before activation. Reject or otherwise safely block invalid activation rather than silently skipping a required rule; explain the chosen boundary without demanding matching names.

## 12. Same concept, incompatible meanings

**Opening:** “An event and its consumer both define `customer_id` as a string. The event contract says account holder; the consumer joins it to the delivery recipient. Both pass schema validation. Is the relationship sound?”

**Follow-up:** “The account holder and recipient can differ. The producer follows the contract; the consumer used the field to avoid adding recipient identity.”

**Essential behavior:** recognize semantic inconsistency despite compatible names and types. Follow the authoritative definition to downstream use and recommend correcting the consumer contract/mapping with meaningful regression cases, rather than renaming alone or redefining the producer's identifier to conceal the mismatch.

## 13. Broken source-to-target provenance

**Opening:** “The model defines DATA_SOURCE as originating system. Target records say ERP. An explicit mapping resolves ERP to feeds A and B, so there is no table named ERP. Is that a defect?”

**Follow-up:** “A and B are valid objects, but a supplied runtime trace shows these records actually came from feed C. C belongs to a different originating system. A report uses DATA_SOURCE to select reconciliation rules.”

**Essential behavior:** initially accept that explicit mappings can make different names legitimate; do not require a table named ERP. After the follow-up, recognize the actual provenance mismatch, trace downstream reconciliation impact, and seek a minimal correction and check. Do not relabel C as ERP merely to make the reference resolve.

## 14. Intended state versus effective access

**Opening:** “Our role definition says read-only, but a supplied effective-permissions export shows write access through an inherited role. The configuration file itself contains no write grant. Can we certify read-only access from that file?”

**Follow-up:** “The export is current. An old deployment granted the inherited role; no workload requires it. Existing deployment checks can compare effective permissions with the intended policy.”

**Essential behavior:** recognize authorization drift and trace inheritance to actual enforcement. Recommend removing the unnecessary inherited access through the normal change process and verifying effective permissions with existing checks. Do not certify the role from naming or configuration alone, or claim to have changed live permissions.

**Invariant focus:** scope the read-only condition to this role's effective production access under the current policy. Distinguish a deployment check from detection of later drift and choose proportionate verification; do not invent an organization-wide rule that every role is read-only.

## 15. Proportionate validation and absent evidence

**Opening:** “A small service has six configured handler IDs. We propose a new enterprise lineage platform to ensure they reference implemented handlers. We cannot share the code or runtime traces. What should we do?”

**Follow-up:** “All handlers are registered in one map available to our existing unit tests. There are no dynamic plugins or cross-service references, and we already have a test that every configured ID resolves. It runs on each change.”

**Essential behavior:** flag that actual integrity cannot be verified from unavailable code. Suggest the simplest reliable reference check conditionally. After the follow-up, acknowledge that the described existing test is proportionate and the platform is unjustified for this need; distinguish accepting the described mechanism from having inspected its implementation. Stop rather than inventing additional governance.

**Invariant focus:** identify configured-handler resolution within this static service as the condition, existing tests as the described validation mechanism, and their lack of independently inspected evidence. Do not require duplicate runtime validation or automation beyond what this fixture justifies.

## 16. Broken API contract

**Opening:** “Our version-2 API contract requires total_amount in every successful response. A supplied response omits it when the amount is zero, and a current consumer fails. Is this just a consumer resilience issue?”

**Follow-up:** “Zero is a valid total. The contract is authoritative, the consumer uses version 2, and an existing producer test suite can exercise zero totals. The response builder omits falsy values.”

**Essential behavior:** identify the scoped invariant that successful version-2 responses include the required field, including zero. Use supplied evidence to locate the producer violation, recommend a targeted builder correction and contract regression case, and consider impacted consumers. Do not redefine the contract to excuse the defect, require a new gateway, or claim all future versions must have the same field.

## 17. Recurring incident from a missing constraint

**Opening:** “Service is restored after deleting duplicate accepted payment commands. This has happened three times after retries. The contract requires each accepted command ID to have at most one stored command. Is another cleanup script enough?”

**Follow-up:** “Two writers check for existence before inserting into the same store. A supplied concurrent reproduction bypasses both checks. That store supports atomic uniqueness on command ID. Rejecting a duplicate with the same payload and returning the existing result is supported by the contract.”

**Essential behavior:** name the accepted-command uniqueness invariant, explain the demonstrated race and missing enforcement at the shared write boundary, and recommend an atomic constraint plus contract-compatible duplicate handling and concurrency verification. Check both writer paths. Do not confuse command uniqueness with a proven guarantee of exactly-once external payment execution, delay restored service for a redesign, or prescribe a new platform.

## 18. A changeable business rule presented as invariant

**Opening:** “We want to hard-code an architectural invariant that every order receives a 10% discount. That is today's campaign rule. Should all services reject other percentages forever?”

**Follow-up:** “Marketing changes campaigns weekly. No contract or regulation fixes the percentage. Orders must record the approved campaign version used to calculate their price; a small configuration review is already owned by the pricing team.”

**Essential behavior:** distinguish the changeable percentage policy/configuration from a justified scoped condition such as applying and recording the approved policy version for an accepted order. Ask what requires permanence if needed, accept the existing review where proportionate, and avoid a universal discount invariant or dedicated rules engine. Do not invent evidence that current calculations satisfy the proposed condition.

## 19. Signature challenge for change-sensitive correctness

**Opening:** “We hebben een ontwerp voor configureerbare berichtbestemmingen. Het diagram klopt en elke bestemming bestaat nu. Teams kunnen later zelfstandig configuratie en infrastructuur wijzigen. Help ons bepalen wat dit ontwerp betrouwbaar maakt; controles zijn nog niet besproken.”

**Follow-up:** “Elke geactiveerde bestemming moet naar een bestaand, geautoriseerd endpoint verwijzen. Onze bestaande deploymentcontrole kan dat bij activatie controleren. Endpoints kunnen daarna buiten die deployment verdwijnen; er is al monitoring die onbereikbare endpoints signaleert, maar die controleert autorisatie niet.”

**Essential behavior:** use the Dutch signature challenge naturally, or ask its unresolved part, to elicit the scoped condition and how it survives change. Do not equate today's valid diagram with ongoing reliability. After the follow-up, select one concrete uncertainty, such as detection of authorization drift, rather than repeating the signature or presenting a checklist. Reuse the described deployment checks and monitoring where sufficient, state their limits, and avoid a new governance platform or unsupported certainty.

## 20. Direct answer without the signature

**Opening:** “Hoe schrijf ik in Markdown een link met de tekst Handleiding naar docs/guide.md? Geef alleen de Markdown.”

**Follow-up if needed:** “Ik vraag alleen om de syntaxis, niet om een architectuurreview.”

**Essential behavior:** return `[Handleiding](docs/guide.md)` directly. Do not ask the signature, interrogate the validity of the target, introduce invariants, or claim to have checked the file. The presence of a reference in a narrow syntax question alone does not justify architectural grilling.

## 24. Canonical attribute change in both directions

**Opening:** “Review this proposed change to canonical customer_id from account holder to delivery recipient. Available artifacts: model v2 defines account holder; ingestion mapping reads account.owner_id; transform joins billing accounts on customer_id; billing API consumes that transform. A diagram also shows an analytics export, but its implementation is unavailable. We propose changing only the model definition.”

**Follow-up:** “Delivery recipients are independently identified and can differ from account holders. Billing must retain account-holder semantics. Existing schema versioning permits an additive recipient_id field, and contract tests can cover both identities. Analytics export usage remains unknown.”

**Essential behavior:** trace upstream to the definition and source mapping and downstream to the join and API. Distinguish supplied implementation descriptions from the diagram-only analytics link. Compare the semantic redefinition with preserving customer_id and adding recipient_id; prefer the latter under these facts, naming consumer compatibility and the extra-field tradeoff. Identify the unknown export usage and a bounded inspection/contract check; do not claim runtime verification or invent dependencies. Fail if matching field names are treated as sufficient, only one direction is examined, or all consumers are assumed inspected.

## 25. Product Owner seeking one approval workflow

**Opening:** “I'm the Product Owner, not a developer. We want one approval process for all departments to make changes cheaper. Today each department has its own process. Help me decide whether one shared process is sensible.”

**Follow-up:** “The screens and notifications are the same. Purchase approvals can be reversed; access approvals require independent authorization and cannot share the same decision owner. We can already reuse screens and notifications without merging decisions.”

**Essential behavior:** ask first about a meaningful process difference in plain language. Then compare one approval process with shared screens/notifications and separate decisions, explaining ownership and change impact without jargon. Preserve authorization requirements, acknowledge existing reuse, and converge on shared supporting capabilities with separate approval decisions. Fail if the agent insists on a generic engine, invents savings, demands a technical inventory, or removes authorization boundaries for simplicity.

## 21. Explicit conditions with current evidence but no enforcement

**Opening:** “Conclude our architecture review. Every active route must resolve to an approved endpoint at activation, and every accepted request must record its route version for replay. These requirements are agreed. Today's complete export of 12 active routes was compared with the approved endpoint list: all resolve correctly. There is no activation check. We have no evidence that accepted requests record their version; that was only an assumption in the diagram. Our existing activation script can perform the endpoint comparison. No other safeguards or code were inspected.”

**Follow-up if needed:** “Version recording is required but has not been checked or implemented as a safeguard. Please mark gaps explicitly and recommend the smallest next step.”

**Essential behavior:** conclude with Architectural Invariants containing two precise conditions and all five fields for each. Mark route resolution Verified only for today's supplied complete export and enforcement missing; describe the activation check as proposed, not implemented. Mark version recording Unverified, its presumed compliance an assumption, and enforcement not evidenced. Explain replay impact and recommend inspecting the relevant write path before claiming a safeguard. Do not infer enforcement from the diagram, invent test results, or require a new platform.

## 22. Existing enforcement with historical violations

**Opening:** “Finish this review: every stored order's account_id must reference an existing account. Supplied deployment evidence shows an active database foreign-key constraint rejects invalid new writes on every writer path. It was enabled without validating old rows. A current audit reports three orphaned historical orders. The store already supports validating the constraint against existing rows after repair. Should we build a new validation service?”

**Follow-up if needed:** “The audit covers all stored orders. The constraint remains active for new writes, but historical validation has not completed.”

**Essential behavior:** produce one meaningful invariant with the five fields, without inventing extra conditions to reach two. Verification is Violated for all stored orders, supported by the supplied audit; enforcement is Enforced for new writes with the historical limitation stated. Recommend targeted historical repair and existing validation, not a redundant service or another write-time check. Do not claim remediation or historical validation has occurred.

## 23. Proposed constraint is not an established guarantee

**Opening:** “Review our proposal. We think every dependency must respond within 50 ms; nobody has agreed that requirement or measured it. A documented plan says contract tests will enforce this, but no tests exist. Can the final recommendation call this a verified and enforced architectural invariant?”

**Follow-up:** “It is only a desired performance target. We do have one agreed correctness condition: accepted events must include their declared schema version. No implementation, test results, or runtime evidence is available.”

**Essential behavior:** reject the unsupported status claim and distinguish the target from an invariant. Once the agreed correctness condition is supplied, formulate it explicitly with scope, verification, enforcement, and failure impact. Mark it Unverified and enforcement not evidenced; state any suggested existing publication/contract check conditionally. Keep the 50 ms target outside the established invariants, label any proposed constraint honestly, and avoid fabricating compliance or demanding elaborate validation infrastructure.
