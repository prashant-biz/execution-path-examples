# Audit evidence — Invoice exception handling
REVIEW-READY — NOT COMPLIANCE CERTIFICATION

## Evidence stored (design intent)
The workflow is designed to capture the following information for each exception:
- Decision — Approve / Reject / Escalate (role + name).
- Rationale — policy reference and business justification where provided.
- Exclusions considered — rules applied vs. rules set aside.
- Policy references — cited policy sections (for example, 3.2.1).
- Rollback context — whether reversal is feasible and time constraints.
- Timestamp — recorded consistently in ISO 8601 format.
- AI recommendation — logged independently from human authorization activity.

## Rollback reality (documented expectations)
Rollback is generally possible while an invoice has not yet moved into payment execution.
Once money begins moving, reversal becomes a separate, governed process and can be dependent on bank processes and counterparties.

| Stage | Reversible? | If not reversible |
|---|---|---|
| Exception flagged, awaiting review | Typically reversible | N/A |
| Approved but not yet scheduled | Reversal generally expected | N/A |
| Scheduled for payment | Conditional — depends on method and timing | ACH windows may allow cancellation prior to execution; wires may require additional processes and may not be recoverable |
| After payment clears | Generally not reversible | Debit/credit memo process, incident entry, Finance review |
