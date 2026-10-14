---
appliesTo:
- {type: capability, id: rename-payee}
- {type: capability, id: delete-payee}
- {type: entity, id: payee}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/transactions/payee-service.ts
---

# Renaming or deleting a payee changes every transaction carrying it

A renamed payee is renamed on every transaction and split line, merging into an existing payee of that name; a deleted payee is cleared from them.
