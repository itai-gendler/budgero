---
appliesTo:
- {type: entity, id: transaction, effect: changes, from: Reconciled, to: Uncleared}
permits: []
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/queries.ts
  title: TransactionQueries.setTransactionsCleared
---

# Nobody marks a reconciled transaction uncleared

A reconciled transaction's cleared status is locked; marking transactions cleared or uncleared leaves reconciled ones untouched.
