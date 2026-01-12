# Deterministic invoice processing workflow
This document does not define policy or certify compliance.

## Single execution path
Inbound invoice → ERP-safe draft.

## 7-stage execution path with SLA & ownership
| Stage | Owner | Action | SLA | Audit |
|---|---|---|---:|---|
| Trigger | System | Record source, timestamp, checksum | Immediate | Provenance log |
| Input | System | Ingest document, extract metadata | < 1 second | Source + metadata |
| Extraction | AI | Bounded field extraction only; no invention | < 10 seconds | Fields + confidence |
| Validation | System | Binary rule checks (pass/fail) | < 2 seconds | Check results + timestamp |
| Decision | System | Route / Hold / Escalate | < 1 second | Decision logic + reason codes |
| Output | System / Human | Create draft or review task | < 5 seconds | Record + authorization |
| Audit | System | Immutable log + history | Real-time | Hash + verification |

## Boundary cases & edge-case handling
| Case | Scenario | Handling | Owner | SLA |
|---|---|---|---|---:|
| OCR failure | Image unreadable/corrupted | Hold → Review task, OCR error flagged | Human | 4 hours |
| Duplicate invoice | Same vendor + number within 90 days | Block → Link prior reference → Log duplicate flag | System | Immediate |
| Multi-currency | Mixed line-item currencies | Flag ambiguity → Route to review with conversion rules | Human | 4 hours |
| Resubmission | Corrected invoice after rejection | Fresh extraction → Link prior rejection → Re-validate | System | < 15 seconds |
| Missing PO | No matching PO found | Escalate to procurement for PO creation/match | Human | 8 hours |
| Totals mismatch detected | Line-item sum ≠ invoice total | Reject → Flag discrepancy → Await vendor correction | System | Immediate |
