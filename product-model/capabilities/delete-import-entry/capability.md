---
domain: imports
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/import/import-history-service.ts
  title: ImportHistoryService.deleteImportRun
---

# Delete import entry

Remove an entry from the import history without touching what it imported.
