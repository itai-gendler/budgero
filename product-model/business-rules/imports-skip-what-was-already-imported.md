---
appliesTo:
- {type: capability, id: import-transactions}
- {type: entity, id: import-run}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/import/duplicate-planner.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/csv-import.mdx
  title: Avoiding duplicates
---

# An import never adds a row it already imported

Rows matching an earlier import are skipped, and rows that may duplicate existing transactions are imported only after the person decides each one.
