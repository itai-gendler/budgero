---
appliesTo:
- {type: capability, id: assign-money}
- {type: capability, id: add-transaction}
- {type: capability, id: edit-transaction}
- {type: capability, id: delete-transaction}
- {type: capability, id: process-push-queue}
- {type: entity, id: audit-log-entry}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/mutation-history/index.ts
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/AuditLogPage.tsx
---

# Every change to a budget is recorded in its audit log

Each change made on a device or synchronised from another is recorded with its time and origin, and pushed operations that fail are recorded with their error.
