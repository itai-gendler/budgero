---
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/BudgetSettingsPage.tsx
- kind: code
  role: implementation
  target: packages/core/src/services/budgets/index.ts
  title: BudgetService.updateGoalFundingSettings
- kind: doc
  role: intent
  target: packages/website/content/docs/ready-to-assign.mdx
  title: Two ways to calculate Ready to Assign
---

# Change budget settings

Change the budget's calculation and assignment settings on the Budget Settings
page: the Ready to Assign mode, goal funding priority choices, sharing within a
priority, priority badges, and whether the workspace allows over-assignment.
Changing a calculation setting never changes transactions or assignments.
