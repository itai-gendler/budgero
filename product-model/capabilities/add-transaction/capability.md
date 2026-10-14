---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/index.ts
  title: TransactionService.addTransaction
- kind: code
  role: implementation
  target: packages/app/src/shared/runtime/app-runtime.ts
  title: applyContinuousRulesIfNeeded
---

# Add transaction

Record a transaction in an account: its date, payee, category, memo and
inflow or outflow. Foreign-currency amounts are converted into the budget's
display currency, and the budget's continuous rules run on the new
transaction.
