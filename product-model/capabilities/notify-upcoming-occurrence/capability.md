---
domain: recurring-transactions
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/recurring/api/useRecurringNotifications.ts
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
  title: RecurringTransactionService.listNotificationCandidates
---

# Notify upcoming occurrence

Remind people on their device before a recurring transaction is due, once
per occurrence, when notifications are enabled for the app. Reminders stay
on the device.
