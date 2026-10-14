---
appliesTo:
- {type: entity, id: occurrence, effect: changes, to: Skipped}
permits:
- {related: [{verb: has, entity: recurring-transaction}, {verb: contains, entity: budget}, {verb: contains, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
  title: RecurringTransactionService.skipOccurrence
---

# Any workspace member skips an occurrence

Every member of the workspace may skip an upcoming occurrence.
