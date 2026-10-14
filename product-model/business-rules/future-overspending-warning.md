---
appliesTo:
- {type: capability, id: assign-money}
- {type: capability, id: move-money}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/monthly-budgets/index.ts
  title: MonthlyBudgetService.checkFutureOverspending
---

# Lowering an assignment warns before a future month goes negative

Before an assignment is lowered or money is moved out of a category, the
Product checks every later month of that category; if any would drop below zero
Available, it lists those months and applies the change only when the person
proceeds.
