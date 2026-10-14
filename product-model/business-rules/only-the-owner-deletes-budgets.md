---
appliesTo:
- {type: entity, id: budget, effect: removes}
permits:
- {related: [{verb: contains, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}], when: [{entity: workspace-membership, fact: Role, is: Owner}]}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-management/ui/BudgetSwitcher.tsx
---

# Only the workspace owner deletes budgets

Members cannot delete a budget.
