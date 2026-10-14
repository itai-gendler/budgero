---
appliesTo:
- {type: capability, id: split-transaction}
- {type: entity, id: transaction, facts: [Split lines]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/split-service.ts
  title: SplitService.upsertSplits
---

# Split lines add up exactly to the transaction

A split transaction's lines always add up to its total to the milliunit, each
line has either a category or a transfer account, and a transfer leg is never
split.
