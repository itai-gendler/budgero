---
domain: budgets
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/budgets/index.ts
  title: BudgetService.updateBudgetCurrency
---

# Edit budget

Change a budget's name, icon, number format or display currency.
