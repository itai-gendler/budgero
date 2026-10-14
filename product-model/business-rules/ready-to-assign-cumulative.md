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
  title: MonthlyBudgetQueries.readyToAssign
- kind: doc
  role: intent
  target: packages/website/content/docs/ready-to-assign.mdx
  title: Cumulative (default)
---

# Ready to Assign is one all-time figure

In Cumulative mode Ready to Assign is the same in every month: all income
dated today or earlier, minus every assignment ever made in any month, minus
money moved off the budget, plus money moved onto it. Overspending stays inside
the category as a negative Available that carries forward until it is covered,
and never touches Ready to Assign.
