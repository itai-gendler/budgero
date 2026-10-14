---
appliesTo:
- {type: entity, id: occurrence, effect: removes}
permits:
- {related: [{verb: has, entity: recurring-transaction}, {verb: contains, entity: budget}, {verb: contains, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
  title: RecurringTransactionService.updateRecurringTransaction
---

# Any workspace member replaces scheduled occurrences by editing a schedule

Scheduled occurrences are removed only when a member changes the recurring schedule or deletes the template.
