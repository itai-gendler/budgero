---
entities:
- {entity: import-run, shows: [Source, Imported at, Transactions created, Accounts created, Categories created, Warnings]}
- {entity: account, shows: [Name]}
entryPoints:
- web-app: /settings/imports
references:
- kind: code
  role: implementation
  target: packages/app/src/pages/settings/ImportsPage.tsx
- kind: code
  role: implementation
  target: packages/app/src/features/import/ui/csv-pdf-dialog/CSVPDFImportDialog.tsx
---

# Imports

Importing a bank file, and the import history with what each import created.
