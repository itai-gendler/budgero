---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/index.ts
  title: TransactionService.deleteTransaction
---

# Delete transaction

Delete a transaction; deleting either leg of a transfer deletes both.
