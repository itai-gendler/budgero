---
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/AuditLogPage.tsx
- kind: code
  role: implementation
  target: packages/core/src/services/mutation-history/index.ts
---

# Audit log entry

One change to a budget as the audit log shows it: what was done, on this
device or synchronised from another, and when.

## Information kept

- **Action** — the change made
- **Origin** — this device or another device
- **Time** — when it happened
- **Error** — why a change that arrived through the Push API could not be applied

## States

### Applied

In effect.

### Undone

Reverted by an undo.
