# Authority boundaries
This documentation makes control boundaries explicit so reviewers can evaluate them.
Authority assignment always remains with policy owners.

| Component | Allowed | Not allowed |
|---|---|---|
| AI | Read documents, extract visible fields, flag ambiguity | Invent values, override rules, make posting decisions |
| Rules Engine | Enforce business constraints, block unsafe actions | Post without validation, make exceptions |
| Humans | Resolve exceptions, correct data, review and authorize posting (per policy) | Approve blindly, bypass validation |
