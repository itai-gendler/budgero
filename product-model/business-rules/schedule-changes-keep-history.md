---
appliesTo:
- {type: capability, id: edit-recurring-transaction}
- {type: entity, id: occurrence, facts: [Due date]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
  title: RecurringTransactionService.updateRecurringTransaction
---

# A schedule change replaces only scheduled occurrences

Changing a recurring schedule regenerates its scheduled occurrences; posted and skipped occurrences and their transactions stay as they are.
