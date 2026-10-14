---
appliesTo:
- {type: capability, id: import-ynab-budget}
- {type: entity, id: import-run, facts: [Warnings]}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/import/ynab-import-service.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/ynab-import.mdx
  title: 'Recommended: connect directly'
---

# A YNAB import is checked against YNAB before it is kept

Every transaction and account balance must match YNAB or the import stops and
its budget is removed; differences in category history or Ready to Assign are
shown and kept only when the person accepts them. The YNAB token is used only
for that import and never stored.
