---
appliesTo:
- {type: capability, id: create-goal}
- {type: entity, id: goal}
references:
- kind: code
  role: implementation
  target: packages/core/src/database/migrations/001-initial-schema.ts
---

# A category has at most one goal

Each category carries at most one goal; changing the target edits that goal.
