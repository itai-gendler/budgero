---
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/shared/mutations/UndoStore.ts
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/AuditLogPage.tsx
---

# Undo change

Revert a recent change to the budget, with the undo shortcut or from the audit
log.
