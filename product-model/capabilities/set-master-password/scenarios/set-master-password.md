---
kind: primary
routes:
  web: Web
steps:
- text: The User enters and confirms a strong master password
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The Product derives the key-encryption key on the device and records that the User has a master password
  kind: product
  actor: user
  entities:
  - {entity: user, effect: changes, facts: [Master password set]}
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The Product continues to the workspaces
  kind: condition
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::master-password
---

# Set a master password

## Trigger

A person signs in for the first time.

## Outcome

Their data can now be encrypted; nobody but them can decrypt it.
