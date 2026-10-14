---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes one or several selected payees
  kind: actor
  actor: user
  entities:
  - {entity: payee, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::payees
- text: The Product removes the Payees and clears them from transactions and split lines in one change
  kind: product
  actor: user
  entities:
  - {entity: payee, effect: removes}
  - {entity: transaction, effect: changes, facts: [Payee, Split lines]}
  contexts:
    web:
      place: web-app::signed-in::payees
---

# Delete payees

## Trigger

A person cleans up junk payees from an import.

## Outcome

The payees are gone and the affected transactions have no payee.
