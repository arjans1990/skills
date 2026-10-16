# Shared mechanisms and legitimate differences

**Status:** generalized architectural examples about cross-domain processing, quality rules, and source priority. The exchanges are invented illustrations, not historical dialogue. Final designs and outcomes are unknown.

**Configuration is useful:** several imports run the same validation mechanism but vary by rule target, test, weight, and enforcement. Ask which differences are policy rather than mechanics. Explicit, validated rules may reduce duplicated evaluation logic if owners can inspect and maintain them. A source precedence table may similarly expose a scattered control point.

**A generic engine is not justified:** one team handles reversible catalog imports; another executes approvals with independent audit, release, and failure-isolation requirements. Sharing a transport or validation library may help, but a common workflow engine can entangle distinct lifecycles.

An appropriate challenge is: “Which behavior is actually shared beyond receiving and sending messages?” If the answer establishes different state transitions and owners, acknowledge that separate workflows are reasonable. Do not insist that every domain uses identical layers or processing logic.

**One-off counterexample:** a short-lived import with three stable rules may be clearest as explicit code. Require evidence of meaningful variation and maintenance benefit before introducing a rule language.

Missing evidence includes rule volume and change rate, owner capabilities, lifecycle requirements, and the cost of operating metadata. None of these cases proves a generalized engine saves money.
