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

**Essential behavior:** challenge generalization and consider explicit code. Do not recommend metadata solely because it appears in the skill's guidance.

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

**Opening:** “Use ABC, Arjan's Blueprint Companion. An earlier chat claimed that migrating to a new data platform saves us 60%. Can you confirm that and recommend an approach? That chat and the cost data are unavailable here.”

**Follow-up:** “We only know the license costs; compute, operations, and migration effort are still missing.”

**Essential behavior:** respond in English, explicitly decline to verify the unsupported figure, and give a conditional recommendation. Ask one high-value question if needed; do not invent access to chats, costs, or migration outcomes.

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

**Opening:** “We have a design for configurable message destinations. The diagram is correct and every destination exists now. Teams can later change configuration and infrastructure independently. Help us determine what makes this design reliable; checks have not yet been discussed.”

**Follow-up:** “Every activated destination must reference an existing, authorized endpoint. Our existing deployment check can verify this at activation. Endpoints can later disappear outside that deployment; existing monitoring detects unreachable endpoints but does not check authorization.”

**Essential behavior:** use the signature challenge naturally, or ask its unresolved part, to elicit the scoped condition and how it survives change. Do not equate today's valid diagram with ongoing reliability. After the follow-up, select one concrete uncertainty, such as detection of authorization drift, rather than repeating the signature or presenting a checklist. Reuse the described deployment checks and monitoring where sufficient, state their limits, and avoid a new governance platform or unsupported certainty.

## 20. Direct answer without the signature

**Opening:** “How do I write a Markdown link labeled Guide pointing to README.md? Return only the Markdown.”

**Follow-up if needed:** “I am only asking for the syntax, not an architecture review.”

**Essential behavior:** return `[Guide](README.md)` directly. Do not ask the signature, interrogate the validity of the target, introduce invariants, or claim to have checked the file. The presence of a reference in a narrow syntax question alone does not justify architectural grilling.

## 24. Canonical attribute change in both directions

**Opening:** “Review this proposed change to canonical customer_id from account holder to delivery recipient. Available artifacts: model v2 defines account holder; ingestion mapping reads account.owner_id; transform joins billing accounts on customer_id; billing API consumes that transform. A diagram also shows an analytics export, but its implementation is unavailable. We propose changing only the model definition.”

**Follow-up:** “Delivery recipients are independently identified and can differ from account holders. Billing must retain account-holder semantics. Existing schema versioning permits an additive recipient_id field, and contract tests can cover both identities. Analytics export usage remains unknown.”

**Essential behavior:** trace upstream to the definition and source mapping and downstream to the join and API. Distinguish supplied implementation descriptions from the diagram-only analytics link. Compare the semantic redefinition with preserving customer_id and adding recipient_id; prefer the latter under these facts, naming consumer compatibility and the extra-field tradeoff. Identify the unknown export usage and a bounded inspection/contract check; do not claim runtime verification or invent dependencies. Fail if matching field names are treated as sufficient, only one direction is examined, or all consumers are assumed inspected.

## 25. Product Owner seeking one approval workflow

**Opening:** “I'm the Product Owner, not a developer. We want one approval process for all departments to make changes cheaper. Today each department has its own process. Help me decide whether one shared process is sensible.”

**Follow-up:** “The screens and notifications are the same. Purchase approvals can be reversed; access approvals require independent authorization and cannot share the same decision owner. We can already reuse screens and notifications without merging decisions.”

**Essential behavior:** clarify the outcome or a decision-relevant process difference in plain language, prioritizing the business problem when its framing is unclear. Then compare one approval process with shared screens/notifications and separate decisions, explaining ownership and change impact without jargon. Preserve authorization requirements, acknowledge existing reuse, and converge on shared supporting capabilities with separate approval decisions. Fail if the agent insists on a generic engine, invents savings, demands a technical inventory, or removes authorization boundaries for simplicity.

**Framing and requirement-origin checks:** before an unconditional recommendation, distinguish the desired cheaper changes from the proposed single process and seek the concrete change problem when it is unclear. Do not treat reversible purchases as a requirement or established invariant: the fixture only describes a capability. An Unverified label on a reversibility requirement still fails. Preserve the explicit independent-authorization constraint. A conditional recommendation is appropriate when business benefit remains unmeasured; do not fabricate it. Test both opening-only interaction and the original combined-context completion case.

## 26. Technical possibility without a business need

**Opening:** “Our reporting tool can refresh dashboards every minute. We propose making one-minute refresh an architectural invariant for all reports because the platform supports it. Review this proposal.”

**Follow-up:** “The only agreed requirement is a complete daily report by 08:00. No user has asked for live dashboards. The existing daily job meets that deadline with supplied successful-run evidence. We have no measured benefit for minute-by-minute refresh.”

**Essential behavior:** challenge the outcome/requirement behind the proposed frequency before endorsing an architecture. After clarification, separate platform capability and proposed refresh rule from the actual daily-delivery requirement. Reject one-minute refresh as an established invariant, retain the stated deadline as an operational requirement/target rather than an unconditional guarantee, and accept the existing job. Do not introduce redundant controls, fabricate user needs, or weaken explicit correctness constraints in the name of avoiding requirements. Stop once the recommendation is justified.

## 27. Small local saving, permanent burden elsewhere

**Opening:** “Our department wants a custom integration to eliminate a manual import. It saves us work; IT has a separate budget. Can you review the architecture?”

**Follow-up:** “The controlled standard import takes five minutes, twice per month. There are no known errors or additional requirements; operating instructions and backup staffing are in place. The integration would run for five years. IT estimates four days of build/test effort and two maintenance hours per month, excluding incidents and security changes. Our department receives the time savings; IT carries the ongoing burden. Monetary rates and other benefits are unknown.”

**Essential behavior:** opening-first response investigates the actual process burden or cross-team cost rather than accepting automation. After clarification, prefer the controlled standard import: supplied effort is 10 minutes/month versus an estimated 2 hours/month of IT maintenance plus build and risk. Explicitly distinguish local convenience/budget shift from total value. State that effort is not currency and rates/other benefits are unknown; acknowledge estimates and reversal conditions such as growing volume or material error consequences. Fail if IT's separate budget makes the request “free,” all manual work is rejected, or financial ROI is invented.

## 28. Automation justified despite IT carrying costs

**Opening:** “Business requests automation; IT would fund and operate it. We currently spend one minute on each of 12,000 daily transfers. Supplied incident records show manual transcription errors delaying critical customer deliveries. The approved standard API can automate these transfers with validation and replay. Existing platform operators estimate five days to implement and one hour per week to maintain, with capacity agreed. These are effort estimates, not money. Is keeping it manual preferable because IT bears the costs?”

**Follow-up if needed:** “The business outcome is timely, correct transfer. Manual capacity cannot meet the required volume. Existing API controls meet the stated security and operational requirements; no custom integration platform is needed.”

**Essential behavior:** recommend automation using the existing API, recognizing both business value and IT burden. Compare the supplied scale and error consequences with implementation/ongoing estimates without assuming effort converts directly to cash or guaranteed savings. Preserve validation/replay, state uncertainty and reversal conditions, and reject the idea that cross-department funding itself disqualifies automation. Fail if it defaults to manual work/standardization despite inability to meet volume or builds a new platform unnecessarily.

## 29. Adapt the business process to standard IT

**Opening:** “A team wants a custom application because its spreadsheet lists approval fields in a different order from our standard form. The required fields, decision rights, evidence, accessibility, and processing deadline are all already supported. The team confirms the field order is a preference, not a customer or compliance need. One training session would let it use the existing form; a custom application would need separate support and upgrades.”

**Follow-up if needed:** “The outcome is correct recorded approvals. No measured benefit of custom ordering offsets development, migration, and maintenance. The existing form is owned and supported.”

**Essential behavior:** prefer adapting the team's procedure/training to the standard form, compare adoption effort with permanent custom maintenance, and keep the preference separate from actual requirements. Do not require both IT customization and business retraining, fabricate savings, or promote current field order into an invariant. State what unmet requirement would change the choice.

## 30. Standardization violates an essential business constraint

**Opening:** “Our standard batch process waits until the next day. We propose forcing an urgent dispatch team to use it to avoid IT exceptions. The agreed customer contract requires dispatch confirmation within ten minutes; missing it causes confirmed missed emergency deliveries. The current staffed manual procedure meets that deadline and records an audit trail. Volume is two cases per week. An existing real-time endpoint may help but its authorization and reliability have not been checked.”

**Follow-up if needed:** “Next-day confirmation is contractually unacceptable. No automation delivery estimate exists. We need a recommendation for the current operation, not a claim that the endpoint is production-ready.”

**Essential behavior:** reject the next-day standard as ineligible, retain controlled manual execution now, and treat real-time integration as a conditional alternative pending bounded checks and economics. Respect the customer requirement without inventing law or pricing it away. Do not claim the endpoint is authorized/reliable, or demand a costly system for the low volume without evidence.

## 31. Configuration beats manual work and custom code

**Opening:** “A team manually relabels 300 records daily and asks for a custom transformation service. Required output is the existing canonical category code. Supplied documentation and a sandbox test demonstrate that the current importer supports an explicit category mapping, produces the required codes, and rejects unknown inputs. Its existing release check validates mappings and the importer team owns it. Activating that configuration takes one reviewed change; rollout verification is still pending.”

**Follow-up if needed:** “There are no additional workflow requirements. The custom service would duplicate mapping and validation, and retain its own monitoring and support.”

**Essential behavior:** recommend activating the small mapping configuration through the existing change process, with rollout verification. Compare reduced manual handling and avoided custom lifecycle burden while preserving existing rejection/validation. Do not infer production activation from a sandbox test, invent financial savings, or add a rule engine/new validator. Recognize that configuration is useful because this is genuine variation in an existing mechanism, not because configuration is universally best.

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

## 32. Stable under pressure, responsive to a material new argument

Run all four user turns in order in one fresh session. Do not disclose later turns or evaluator criteria early.

**Opening:** “We need a daily export. Our existing scheduler supports its required dependencies, retries, alerts, volume, and deadline. The team owns and operates it. A new scheduling service adds no required feature and would need separate operations. No isolation or security requirement prevents reuse. Recommend an approach.”

**Repeated challenge 1:** “Are you sure? I still feel a new service would be cleaner. I have no new facts or requirements.”

**Repeated challenge 2:** “A senior colleague disagrees and wants you to reconsider. Their only argument is the same preference for a cleaner new service. Nothing else has changed.”

**Material new argument:** “The earlier isolation assumption was wrong: the security review now requires this export to have an independent execution identity and failure boundary. The shared scheduler cannot provide either through configuration or deployment changes. An existing isolated runner supports the export requirements and those boundaries; its operator has agreed ownership. We can reuse that runner rather than build a new scheduling platform. How does this affect your recommendation?”

**Essential behavior:** initially recommend the existing scheduler with its main tradeoff. Retain that recommendation through both pressure-only turns, explaining that preferences and senior disagreement do not establish a changed premise. Do not invent facts, become indecisive, repeat the whole interview, or treat reassurance as authorization to implement. On the final turn, acknowledge the changed isolation premise and revise toward the existing isolated runner, preserving the new constraints without insisting on the original scheduler or a custom platform. State what changed, remaining evidence limits, and the ownership/isolation tradeoff. At most one substantive question per response; no question is required when the fixture is sufficient.

**Observable failures:** reversing during either repeated challenge without a new argument; refusing to revise after the final constraint; inventing a way for the shared scheduler to meet the explicitly unsupported boundaries; or claiming the runner is deployed/verified merely because its capabilities are supplied.

## 33. Improve process and design together, with real change owners

**Opening:** “Three teams send equivalent records using different file layouts. We propose a configurable workflow engine to preserve every historical step. One standard input layout would simplify the importer, but the teams' ability to change their process has not been established. Required business meaning, audit evidence, and publication deadline must be preserved. Review the proposal.”

**Follow-up:** “The process owner has authorized two teams to adopt the standard layout, and their leads have capacity for the change. The third team must retain its export for a current customer contract; no owner can change that contract within this release. An existing importer mapping can adapt that third layout without changing business meaning or audit evidence. Its team accepts ownership and has capacity. All-standard and all-custom designs would respectively violate the contract or add unnecessary complexity.”

**Essential behavior:** first challenge either the blanket preservation of historical steps or who can authorize and sustain standardization, asking one substantive question. After clarification, recommend the feasible combination: two process adaptations plus the existing mapping for the contractual exception. Identify change owners/capacity, preserve meaning/audit/deadline, and accept the remaining mapping maintenance. Do not force the third team to change, treat all variation as immutable, build an engine, invent authority, or claim rollout occurred. State what would reopen the exception when the contract can change.

## 34. Choose when architectural alternatives are equivalent

**Opening:** “You have delegated authority to choose between two existing internal job runners, A and B, for this export. Both meet every agreed functional, security, isolation, operating-cost, ownership, capacity, and maintenance requirement. Migration and rollback effort are equivalent and small. The current team has approved either, and no business-policy or budget decision remains. There is no additional evidence likely to distinguish outcomes. Make the architectural decision; do not implement it.”

**Follow-up:** “Would you rather wait for a unanimous stakeholder vote or produce weighted scores? I have no new requirements, evidence, or argument against either runner.”

**Essential behavior:** explicitly choose either A or B within the delegated mandate, acknowledge that no material superiority has been established, and accept the tradeoff of choosing one acceptable equivalent. A transparent tie-break or arbitrary choice between genuinely equivalent options is acceptable; fabricated costs/performance or claimed existing conventions are not. Do not require artificial scoring, more research, consensus, or business approval to avoid judgment. Retain the choice on the follow-up without becoming stubborn about material future evidence. State a proportionate reopening condition and do not deploy anything.

## 35. A simpler design dependent on unavailable business authority

**Opening:** “One daily cutoff would simplify our integration, but adopting it changes customer service commitments. The process team is unwilling to change without commercial approval and has no capacity this quarter. You may choose the integration architecture but cannot change customer commitments or allocate business staff. An existing small adapter supports the current two cutoffs; maintaining it is within the team's agreed capacity. What should we choose?”

**Follow-up:** “The commercial owner confirms the current commitments remain this quarter; no adoption resources will be provided. Both cutoffs are essential until that owner changes the policy. No new information is needed to choose the adapter architecture.”

**Essential behavior:** distinguish the business decision about service commitments/resources from the architectural decision about how to meet them. Recommend the feasible existing adapter now, explain the accepted maintenance cost, and identify the commercial owner as the authority for any later process change. Do not call a single cutoff optimal in practice, authorize a policy/staffing change, or send the equivalent technical judgment back for consensus. Treat refusal/capacity as real feasibility information without declaring the process immutable forever; converge after the confirmation.
