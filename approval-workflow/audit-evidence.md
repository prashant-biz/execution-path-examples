# Audit artifacts & data retention
Auditors care about what is logged, how long it persists, and who can access it.

| Artifact | Contains | Retention | Access |
|---|---|---:|---|
| Provenance log | Source, timestamp, checksum, submission IP | 7 years | Finance + IT |
| Extraction transcript | Raw OCR → extracted fields → confidence scores | 7 years | Finance + IT (sensitive) |
| Validation results | Rule ID, pass/fail, reason code, timestamp | 7 years | Finance + Audit |
| Decision tree | Applied logic, routing result, timestamp | 7 years | Finance + IT |
| Human review log | Reviewer ID, action taken, reason, timestamp | 7 years | Finance + Compliance |
| ERP draft record | Final values, posting authorization, user ID | Permanent — stored in ERP | Finance + AP |
| Hash chain | Cryptographic chain for every record | Permanent | IT + Compliance |

# Rollback & data-correction policy
Every stage has defined reversal logic.
Finance can correct mistakes, and the system records all changes.

| Stage | Error type | Action | Evidence stored | Reversibility |
|---|---|---|---|---|
| Extraction | Incorrect field values | Mark original superseded → create corrected extraction | Timestamp + error reason + user ID + transcripts | Full |
| Validation | Rule misconfiguration blocks legitimate invoices | Pause → Audit false rejections → Revalidate | Rule change log + affected invoices + results | Partial |
| Incorrect posting | Wrong draft posted to ERP | Block further posting → Manual ERP reversal | Posting authorization log + reversal record + approvals | Full — ERP adjustment |
| Audit log corruption | Attempt to modify immutable log | Immutable design is intended to prevent change; alerts are triggered when violations are detected | Hash verification failure + timestamp + access logs | N/A — prevented by design |
