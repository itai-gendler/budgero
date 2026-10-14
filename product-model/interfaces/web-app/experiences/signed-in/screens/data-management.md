---
entities:
- {entity: workspace, shows: [Name]}
entryPoints:
- web-app: /settings/data
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/DataManagementPage.tsx
---

# Data management

Exporting a workspace's data and restoring a database backup into it.
