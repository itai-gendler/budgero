---
appliesTo:
- {type: entity, id: budget, effect: changes, facts: [Name, Icon, Number format, Display currency]}
permits:
- {related: [{verb: contains, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}], when: [{entity: workspace-membership, fact: Role, is: Owner}]}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/budget-management/ui/WorkspaceBudgetList.tsx
---

# Only the workspace owner edits a budget's name, icon, number format or currency

Members do day-to-day budgeting but cannot manage the budget itself.
