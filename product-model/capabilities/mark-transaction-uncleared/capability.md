---
domain: accounts
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/queries.ts
  title: TransactionQueries.setTransactionsCleared
---

# Mark transaction uncleared

Return a cleared transaction to uncleared.
