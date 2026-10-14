---
kind: validation
routes:
  web: Web
steps:
- text: The User runs a statement that is not a read-only query
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::explorer
- text: The Product refuses to run it
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::explorer
---

# Refuse a query that would change data

## Trigger

A person tries to edit data from the Explorer.

## Outcome

Nothing changes.
