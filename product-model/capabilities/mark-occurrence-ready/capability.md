---
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
  title: RecurringTransactionService.markOccurrenceReady
- kind: code
  role: implementation
  target: packages/app/src/features/transactions/ui/RecurringOccurrenceActions.tsx
- kind: code
  role: implementation
  target: packages/app/src/shared/runtime/app-runtime.ts
  title: applyContinuousRulesIfNeeded
---

# Mark occurrence ready

Post one occurrence of a recurring transaction as a real transaction, dated on
its due date, from the Recurring Transactions page or an account's upcoming
panel. The budget's continuous rules run on what it posts.
