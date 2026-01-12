# Escalation & ownership — Invoice exception handling
REVIEW-READY — NOT COMPLIANCE CERTIFICATION

## Pause protocol (documented behavior)
When required data is missing (PO, vendor match, amount discrepancies):
1. The system is configured to pause the invoice.
2. A responsible role is assigned in the workflow.
3. A timer is started where supported.
4. Unresolved items are escalated according to configuration.

## SLA boundaries (configuration, not guarantees)
| Exception type | Owner assigned | Escalation expectation | Typical resolution window |
|---|---|---:|---:|
| Missing PO | AP Manager | 24 hours | 48 hours |
| Duplicate flagged | Compliance | 48 hours | 72 hours |
| Variance >10% | Controller | 48 hours | 72 hours |
| Vendor incomplete | Procurement | 5 business days | Varies by onboarding status |

## Approval authority matrix (documented for review)
This matrix documents the approval limits currently associated with roles and the typical override conditions discussed during design review.
Actual authority remains defined by organizational policy and governance processes.

| Role | Max approval (per transaction) | Override context | Requires co-sign |
|---|---:|---|---|
| AP Specialist | $5,000 | None | No |
| AP Manager | $25,000 | Minor deviations (missing dept code, small variance) | No |
| Controller | $100,000 | Material risk (duplicate candidate, vendor warning) | Yes — Legal review |
| CFO | Unlimited | Rare exceptions (policy interpretation, strategic vendor) | Yes — Board audit record |
