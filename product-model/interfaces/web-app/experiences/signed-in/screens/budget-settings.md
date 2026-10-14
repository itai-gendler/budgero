---
entities:
- {entity: budget, shows: [Ready to Assign mode, Priority choices, Sharing within a priority, Show priority badges], collects: [Ready to Assign mode, Priority choices, Sharing within a priority, Show priority badges]}
- {entity: workspace, shows: [Allow over-assignment], collects: [Allow over-assignment]}
- {entity: category, shows: [Name], collects: [Name]}
entryPoints:
- web-app: /settings/budget
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/BudgetSettingsPage.tsx
---

# Budget settings

The budget's calculation and assignment settings: Ready to Assign mode, goal funding, income categories and over-assignment.
