---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Remove splits
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product clears the split lines and removes any mirrored transfer Transaction they created
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: split-transaction, effect: changes, facts: [Split lines]}
  - {entity: transaction, as: mirror, effect: removes, from: Uncleared}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Remove a transaction's splits

## Trigger

A person no longer wants an entry split.

## Outcome

The transaction counts in its own category again.
