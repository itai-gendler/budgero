---
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
  title: RecurringTransactionService.skipOccurrence
---

# Skip occurrence

Drop one occurrence without changing the schedule.
