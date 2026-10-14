---
appliesTo:
- {type: capability, id: mark-occurrence-ready}
- {type: entity, id: transaction, facts: [Date]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
  title: RecurringTransactionService.markOccurrenceReady
---

# A posted occurrence is dated on its due date

The transaction an occurrence posts carries the occurrence's due date, whenever it is marked ready.
