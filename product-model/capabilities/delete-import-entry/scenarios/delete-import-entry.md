---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes an import history entry and confirms
  kind: actor
  actor: user
  entities:
  - {entity: import-run, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::imports
- text: The Product removes the Import entry; its transactions remain
  kind: product
  actor: user
  entities:
  - {entity: import-run, effect: removes, from: Completed}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::imports
---

# Delete an import history entry

## Trigger

A person tidies the import history.

## Outcome

The entry is gone and can no longer be undone; the data stays.
