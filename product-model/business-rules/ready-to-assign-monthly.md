---
appliesTo:
- {type: capability, id: assign-money}
- {type: capability, id: fund-goals}
- {type: capability, id: cover-overspending}
- {type: entity, id: budget, facts: [Ready to Assign]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/monthly-budgets/queries.ts
  title: MonthlyBudgetQueries.readyToAssignMonthlyBatch
- kind: code
  role: implementation
  target: packages/core/node-tests/rta-monthly.node.spec.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/ready-to-assign.mdx
  title: Monthly (YNAB-style)
---

# Ready to Assign is computed through the viewed month

In Monthly mode Ready to Assign is calculated for the month being viewed:
income up to and including that month, minus assignments made up to and
including that month, minus money moved off the budget, plus money moved onto
it, minus cash overspending of earlier months. Assignments made in later months
do not lower an earlier month; they count when their own month is reached. A
category's cash overspending is taken from the next month's Ready to Assign and
the category starts that month at zero; credit card overspending becomes card
debt and shows as an underfunded credit card payment category instead.
