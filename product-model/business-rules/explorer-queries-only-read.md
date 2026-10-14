---
appliesTo:
- {type: capability, id: run-query}
- {type: capability, id: save-report}
- {type: entity, id: report}
references:
- kind: code
  role: implementation
  target: packages/app/src/shared/lib/sql/read-only.ts
---

# Explorer queries only read

The Explorer runs only read-only queries; nothing in the budget can be changed from it.
