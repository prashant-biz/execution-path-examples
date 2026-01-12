# Decision boundary — Invoice exception handling
REVIEW-READY — NOT COMPLIANCE CERTIFICATION

## Boundary principle
Final authorization remains with named human roles, consistent with existing governance.
AI recommendations are advisory inputs.
Decisions are made by people.
Accountability for decisions remains with governance roles, not automation.

## Logging boundary (separate record streams)
AI recommendations and human decisions are recorded in separate log streams.
Divergence events (override or proceeding despite a flag) are recorded side-by-side.
Logs support transparency and do not replace governance review.
