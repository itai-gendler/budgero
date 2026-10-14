---
appliesTo:
- {type: capability, id: restore-backup}
- {type: entity, id: user, facts: [Workspace access]}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/DataManagementPage.tsx
---

# Only the workspace owner with workspace access restores a backup

Restoring replaces every budget of the workspace for all members, so only its owner may do it, and only while they have workspace access.
