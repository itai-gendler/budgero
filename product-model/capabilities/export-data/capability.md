---
domain: data-management
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/DataManagementPage.tsx
- kind: code
  role: implementation
  target: packages/core/src/services/export/index.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/csv-import.mdx
  title: Exporting your data
---

# Export data

Download a workspace's data on the device, as a CSV bundle or a database
backup.
