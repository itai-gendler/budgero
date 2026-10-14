---
kind: primary
routes:
  web: Web
steps:
- text: The User enters the current master password and a new one twice
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::security
- text: The Product verifies the current password and re-wraps each Workspace key under the new one
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  - {entity: user, effect: reads, facts: [Master password set]}
  contexts:
    web:
      place: web-app::signed-in::security
- text: The Product notifies the User's other devices and reloads
  kind: condition
  entities:
  - {entity: user, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::security
---

# Change the master password

## Trigger

A person rotates their master password or suspects it leaked.

## Outcome

The data is preserved and protected by the new password.
