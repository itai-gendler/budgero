---
kind: primary
routes:
  web: Web
steps:
- text: The User picks a file, its header row and the destination account and maps its columns to date, amount or inflow and outflow, and the optional fields
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::imports
- text: The Product previews every row as New, Already imported, Needs review or Invalid
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: [Date, Inflow, Outflow, Payee, Memo]}
  contexts:
    web:
      place: web-app::signed-in::imports
- text: The User decides Skip or Import as new for every row that needs review and imports
  kind: actor
  actor: user
  entities:
  - {entity: import-run, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::imports
- text: The Product records the new rows as cleared Transactions, without a category in Uncategorized, and runs continuous rules on them
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: creates, to: Cleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount]}
  - {entity: rule, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::imports
- text: The Product records the Import in the import history
  kind: product
  actor: user
  entities:
  - {entity: import-run, effect: creates, to: Completed, facts: [Source, Imported at, Transactions created, Accounts created, Categories created]}
  contexts:
    web:
      place: web-app::signed-in::imports
---

# Import a bank file

## Trigger

A person downloads last month's statement from their bank.

## Outcome

The statement's transactions are in the account; already-imported rows were skipped.

## Edge cases

- Dates and number formats are detected across common conventions and can be set by hand.
- A PDF statement first asks which extracted table to use.
- Rows the file marks as not cleared are imported uncleared.
