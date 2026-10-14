---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/index.ts
  title: TransactionService.setTransactionsCleared
- kind: code
  role: implementation
  target: packages/app/src/features/transactions/ui/ClearedToggle.tsx
---

# Mark transaction cleared

Mark one or more transactions as cleared once they appear at the bank.
