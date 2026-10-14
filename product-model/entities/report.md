---
domain: explorer
references:
- kind: code
  role: implementation
  target: packages/core/src/services/reports/index.ts
---

# Report

A named read-only query over the budget's data in the Explorer, with the
charts drawn from its result.

## Information kept

- **Name** — the report name, unique
- **Description** — what it shows
- **Query** — the read-only query
- **Charts** — the charts configured on its result
- **Favorite** — whether it is marked as a favourite
