---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/index.ts
  title: TransactionService.updateTransactionColumn
---

# Edit transaction

Change a transaction's date, payee, memo, category or amount, or move it to
another account.
