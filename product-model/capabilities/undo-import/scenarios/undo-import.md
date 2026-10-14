---
kind: primary
routes:
  web: Web
steps:
- text: The User undoes an import from the history and confirms
  kind: actor
  actor: user
  entities:
  - {entity: import-run, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::imports
- text: The Product removes the transactions, accounts and categories it created, recalculates the affected accounts and marks the Import undone
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: removes, from: Cleared}
  - {entity: import-run, effect: changes, from: Completed, to: Undone, facts: []}
  - {entity: category, effect: reads, facts: []}
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::imports
---

# Undo an import

## Trigger

The wrong file was imported.

## Outcome

The budget is as it was before the import.

## Edge cases

- Undoing an import that is already undone changes nothing.
