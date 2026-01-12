# Workflow Governance Slice — Decision Boundary

## Context
AI helps classify and recommend decisions.
Deals stall when reviewers cannot reconstruct why an action happened.
This slice documents the boundary where AI stops reasoning and the workflow switches into deterministic, auditable control.

## Where AI stops and control begins
[Input]
↓
AI Classification (read-only)
↓
No approvals, no mutations, no state changes. AI outputs are advisory only.
Control logic determines the next governed step.
↓
DECISION BOUNDARY
Are controls satisfied?
✓ YES → Standard (system-driven)
✗ NO → Failure Path (owned, logged)

## Boundary rules
AI MAY:
- Classify (read-only).
- Recommend.
- Flag risk.

AI MAY NOT:
- Approve.
- Override.
- Infer missing data.
- Bypass escalation.

Boundary changes are subject to documented governance approval.
Exception overrides are logged as exception events and routed for Control Owner authorization per policy.

## Failure paths become first-class citizens
| Condition | System action | Owner | SLA | Evidence logged |
|---|---|---|---:|---|
| Missing PO | Stop + request | AP Ops | 2 days | Request thread |
| Totals mismatch | Lock + review | Finance | 3 days | Correction note |
| Vendor anomaly | Escalate | Risk Ops | 5 days | Risk note |
| Duplicate | Freeze + reconcile | Finance | 2 days | Decision note |

SLA breaches are configured to auto-escalate to the Control Owner where implemented.
Escalation: automatic alert + Escalation Queue + timestamp.

## What gets recorded & rollback policy
All post-boundary actions are designed to be traceable and reversible where possible.
Rollbacks produce their own audit entries and do not overwrite prior records.
AI output • Rule result • Actor • Timestamp • Justification • Reversible?

## Boundary ownership
Process Owner: Finance Operations
Control Owner: Risk / Internal Audit
Technical Owner: Product / Engineering

## Reviewer checklist
- Reviewers confirm AI does not approve.
- Ambiguous cases are routed into named failure paths.
- Each path is designed with SLA and evidence logging.
- SLA breaches are configured to escalate automatically.
- Decisions reconstructable end-to-end.
- Rollbacks logged as independent events.
- Boundary changes require policy approval.

## Trade-off
Ambiguous cases may move slower by design.
Predictability and audit trace justify the delay.
