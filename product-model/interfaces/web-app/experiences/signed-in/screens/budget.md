---
entities:
- {entity: budget, shows: [Ready to Assign, Ready to Assign mode]}
- {entity: category-group, shows: [Name], collects: [Name]}
- {entity: category, shows: [Name, Funding priority, Activity, Available], collects: [Name, Funding priority, Exclude from budget pace]}
- {entity: assignment, shows: [Amount, Month], collects: [Amount]}
- {entity: goal, shows: [Target type, Target amount, Needed this month, Status], collects: [Target type, Target amount, Start date, Target date, Repeats]}
- {entity: transaction, shows: [Date, Payee, Inflow, Outflow]}
entryPoints:
- web-app: /budgeting
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/budgeting/BudgetingPage.tsx
- kind: code
  role: implementation
  target: packages/app/src/features/budget-planning/ui/BudgetTable.tsx
---

# Budget

The budget table for one month: Ready to Assign, every category group and category with its assigned amount, activity and available balance, goals, and the Assign menu of quick funding actions.
