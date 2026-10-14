---
appliesTo:
- {type: capability, id: add-transfer}
- {type: capability, id: delete-transaction}
- {type: capability, id: mark-occurrence-ready}
- {type: entity, id: transaction, facts: [Transfer link]}
references:
- kind: code
  role: implementation
  target: packages/app/src/shared/mutations/op-code-registry/domains/transactions.ts
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/index.ts
  title: TransactionService.deleteTransaction
---

# A transfer's two legs are created and deleted together

Both legs of a transfer share one transfer link; they are recorded together,
a failure recording the second removes the first, and deleting either deletes
both.
