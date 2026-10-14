---
appliesTo:
- {type: capability, id: create-budget}
- {type: capability, id: edit-budget}
- {type: entity, id: budget, facts: [Display currency]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/budgets/index.ts
  title: BudgetService.createBudget
---

# A budget's display currency is a fiat currency

The display currency every amount is converted into is always a fiat currency; cryptocurrencies are allowed only as account currencies.
