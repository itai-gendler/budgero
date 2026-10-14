---
appliesTo:
- {type: capability, id: assign-money}
- {type: capability, id: move-money}
- {type: entity, id: category, facts: [Available]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/monthly-budgets/queries.ts
  title: MonthlyBudgetQueries.getMonthlyBudget
- kind: doc
  role: intent
  target: packages/website/content/docs/categories.mdx
  title: The three numbers
---

# A category's Available carries into the next month

A category's Available is its balance from earlier months plus this month's
assignment minus this month's activity, counting only on-budget accounts.
Leftover money rolls forward automatically; how overspending carries depends on
the budget's Ready to Assign mode.
