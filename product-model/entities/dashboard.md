---
domain: custom-dashboards
relations:
- {entity: widget, verb: has, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/custom-dashboards/index.ts
---

# Dashboard

A custom dashboard of pinned report charts.

## Information kept

- **Name** — the dashboard name, unique in the budget ignoring case
- **Position** — its place among the budget's dashboards
