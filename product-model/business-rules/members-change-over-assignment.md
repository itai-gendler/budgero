---
appliesTo:
- {type: entity, id: workspace, effect: changes, facts: [Allow over-assignment]}
permits:
- {related: [{verb: has, entity: workspace-membership}, {verb: holds, entity: user}]}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/BudgetSettingsPage.tsx
---

# Any workspace member changes whether over-assignment is allowed

Owners and members alike may turn over-assignment on or off for the workspace.
