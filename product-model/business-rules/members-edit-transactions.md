---
appliesTo:
- {type: entity, id: transaction, effect: changes}
permits:
- {related: [{verb: holds, entity: account}, {verb: contains, entity: budget}, {verb: contains, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}]}
references:
- kind: doc
  role: intent
  target: packages/website/content/docs/sharing.mdx
  title: Roles
---

# Any workspace member edits transactions

Day-to-day budgeting is shared: every member of the workspace changes the transactions of its budgets.
