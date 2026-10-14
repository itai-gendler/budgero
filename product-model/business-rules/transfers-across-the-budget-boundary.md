---
appliesTo:
- {type: capability, id: add-transfer}
- {type: capability, id: mark-occurrence-ready}
- {type: entity, id: budget, facts: [Ready to Assign]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/monthly-budgets/queries.ts
  title: MonthlyBudgetQueries.readyToAssign
---

# Transfers move Ready to Assign only across the budget boundary

A transfer leg in the Transfers category lowers Ready to Assign when it
leaves an on-budget account for an off-budget account that is not a credit
card, loan or mortgage, and raises it when it arrives from one. Transfers
between on-budget accounts change nothing; a transfer leg the person
categorised to a spending category counts as spending in that category.
