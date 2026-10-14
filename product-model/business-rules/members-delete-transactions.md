---
appliesTo:
- {type: entity, id: transaction, effect: removes}
permits:
- {related: [{verb: holds, entity: account}, {verb: contains, entity: budget}, {verb: contains, entity: workspace}, {verb: has, entity: workspace-membership}, {verb: holds, entity: user}]}
references:
- kind: doc
  role: intent
  target: packages/website/content/docs/sharing.mdx
  title: Roles
---

# Any workspace member deletes transactions

Every member of the workspace may delete the transactions of its budgets.
