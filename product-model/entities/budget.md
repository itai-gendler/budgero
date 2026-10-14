---
domain: budgets
relations:
- {entity: category-group, verb: contains, cardinality: one-to-many}
- {entity: account, verb: contains, cardinality: one-to-many}
- {entity: recurring-transaction, verb: contains, cardinality: one-to-many}
- {entity: rule, verb: contains, cardinality: one-to-many}
- {entity: payee, verb: contains, cardinality: one-to-many}
- {entity: label, verb: contains, cardinality: one-to-many}
- {entity: custom-rate, verb: contains, cardinality: one-to-many}
- {entity: import-run, verb: contains, cardinality: one-to-many}
- {entity: scenario, verb: contains, cardinality: one-to-many}
- {entity: dashboard, verb: contains, cardinality: one-to-many}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/budgets/index.ts
- kind: code
  role: implementation
  target: packages/core/src/services/monthly-budgets/index.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/ready-to-assign.mdx
  title: Ready to Assign
---

# Budget

One zero-based budget inside a workspace: its categories, accounts and
transactions, the money assigned month by month, and the settings that decide
how Ready to Assign and goal funding are calculated.

## Information kept

- **Name** — the budget name
- **Display currency** — the fiat currency every amount is converted into for budgeting
- **Icon** — the badge shown next to the budget name
- **Number format** — how amounts are written
- **Ready to Assign mode** — Cumulative (default) or Monthly
- **Priority choices** — Five levels (default) or Numeric: which funding priorities categories may take
- **Sharing within a priority** — Proportional shortfalls (default) or Equal completion percentage: how Fund Goals shares money that runs out inside one priority tier
- **Show priority badges** — whether non-default funding priorities are shown beside category names; on by default
- **Ready to Assign** — derived: income and money moved onto the budget, minus everything assigned and money moved off the budget, calculated per the Ready to Assign mode
