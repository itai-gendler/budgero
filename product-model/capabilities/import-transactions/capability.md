---
domain: imports
availability:
- {place: 'web-app::signed-in'}
references:
- kind: code
  role: implementation
  target: packages/app/src/features/import/ui/csv-pdf-dialog/CSVPDFImportDialog.tsx
- kind: code
  role: implementation
  target: packages/core/src/services/import/duplicate-planner.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/csv-import.mdx
  title: CSV Import & Export
---

# Import transactions

Import a bank file — CSV, TSV, TXT, OFX, QFX, QIF, CAMT.053 or a PDF statement
table — by mapping its columns, previewing every row against earlier imports
and existing transactions, and deciding on possible duplicates.
