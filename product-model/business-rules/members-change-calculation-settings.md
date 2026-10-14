---
appliesTo:
- {type: entity, id: budget, effect: changes, facts: [Ready to Assign mode, Priority choices, Sharing within a priority, Show priority badges]}
permits:
- {related: [{verb: contains, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}]}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/BudgetSettingsPage.tsx
---

# Any workspace member changes a budget's calculation settings

The Ready to Assign mode and goal funding settings are open to every member of the budget's workspace.
