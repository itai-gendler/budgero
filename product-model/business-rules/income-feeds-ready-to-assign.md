---
appliesTo:
- {type: capability, id: add-transaction}
- {type: capability, id: reconcile-account}
- {type: entity, id: budget, facts: [Ready to Assign]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/monthly-budgets/queries.ts
  title: MonthlyBudgetQueries.readyToAssign
---

# Only income-group inflows on on-budget accounts are income

Ready to Assign counts as income only the net of transactions categorised in
a category of the Income group, on on-budget accounts, that are not transfer
legs. Inflows categorised elsewhere raise that category's Available instead, and
nothing recorded on an off-budget account reaches the budget.
