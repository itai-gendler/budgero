---
kind: validation
routes:
  web: Web
steps:
- text: The User enters a master password and chooses Unlock
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: It does not decrypt the workspace key
  kind: condition
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The Product refuses and keeps the data locked
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::master-password
---

# Refuse a wrong master password

## Trigger

A person mistypes their master password.

## Outcome

The data stays encrypted.
