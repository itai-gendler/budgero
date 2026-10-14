---
domain: imports
references:
- kind: code
  role: implementation
  target: packages/core/src/services/import/import-history-service.ts
- kind: doc
  role: intent
  target: packages/website/content/docs/csv-import.mdx
  title: CSV Import & Export
---

# Import

One import of a bank file or a YNAB budget, kept in the import history with
what it created so it can be undone.

## Information kept

- **Source** — CSV, TSV, TXT, OFX, QFX, QIF, CAMT.053, PDF statement, YNAB export or YNAB direct connection
- **Imported at** — when it ran
- **Transactions created** — the transactions it added
- **Accounts created** — the accounts it added
- **Categories created** — the categories it added
- **Warnings** — for a YNAB import, the differences from YNAB the person accepted

## States

### In progress

Running, or interrupted before it finished.

### Completed

Finished.

### Completed with warnings

A YNAB import saved after the person accepted its differences.

### Undone

Everything it created was removed.
