---
entities:
- {entity: audit-log-entry, shows: [Action, Origin, Time, Error]}
entryPoints:
- web-app: /settings/audit-log
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/AuditLogPage.tsx
---

# Audit log

Every recorded change to the budget, newest first, with the ability to undo recent ones.
