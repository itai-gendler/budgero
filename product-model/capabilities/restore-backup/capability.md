---
domain: data-management
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/DataManagementPage.tsx
  title: handleRestoreDatabase
---

# Restore backup

Replace the active workspace's data with a database backup, upgrading it to the
current format.
