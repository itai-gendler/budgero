---
domain: imports
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/core/src/services/import/import-history-service.ts
  title: ImportHistoryService.undoImportRun
---

# Undo import

Remove everything an import created.
