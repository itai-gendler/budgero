---
domain: budget
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/budget-table/useCategoryOperations.ts
  title: handleUpsertAssignment
- kind: code
  role: implementation
  target: packages/core/src/services/monthly-budgets/index.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/assign-money.mdx
  title: Assigning Money
---

# Assign money

Give a category money for the month being viewed by typing into its Assigned
amount, which works as a small calculator (+, −, ×, ÷ on the current value).
Assigning draws from Ready to Assign; lowering an assignment returns the
difference to it. A future month can be funded ahead of time.
