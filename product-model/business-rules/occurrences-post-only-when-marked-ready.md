---
appliesTo:
- {type: entity, id: occurrence, effect: changes, to: Ready}
permits:
- {related: [{verb: has, entity: recurring-transaction}, {verb: contains, entity: budget}, {verb: contains, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/recurring/index.ts
  title: RecurringTransactionService.markOccurrenceReady
- kind: doc
  role: intent
  target: packages/website/content/docs/recurring-transactions.mdx
  title: Recurring transactions
---

# Only a person posts a recurring occurrence

An occurrence becomes a transaction only when a signed-in person marks it ready; Budgero never posts one on its own schedule.
