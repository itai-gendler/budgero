---
domain: recurring-transactions
relations:
- {entity: transaction, verb: posts, cardinality: one-to-one}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
---

# Occurrence

One due date of a recurring transaction. Budgero keeps occurrences about six
months ahead; each waits until someone posts or skips it.

## Information kept

- **Due date** — the date the occurrence is due; a posted transaction is dated on it
- **Notified at** — when the reminder for it was shown, if it has been

## States

### Scheduled

Upcoming or overdue, waiting to be posted or skipped; projected into forecasts.

### Ready

Posted as a real transaction.

### Skipped

Dropped this time without touching the schedule.
