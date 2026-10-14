---
domain: budgets
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/budgets/index.ts
  title: BudgetService.createBudget
- kind: code
  role: implementation
  target: packages/app/src/features/budget-management/ui/BudgetSwitcher.tsx
- kind: doc
  role: intent
  target: packages/website/content/docs/category-groups.mdx
  title: What you get out of the box
---

# Create budget

Create a budget in the active workspace with a name, display currency, icon and
number format, with or without starter categories. The system groups and
categories are always created.
