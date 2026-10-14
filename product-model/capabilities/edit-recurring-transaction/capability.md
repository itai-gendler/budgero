---
domain: recurring-transactions
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
  title: RecurringTransactionService.updateRecurringTransaction
---

# Edit recurring transaction

Change a recurring template's details or schedule.
