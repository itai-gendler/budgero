---
kind: validation
routes:
  web: Web
steps:
- text: The User submits the change form
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::security
- text: The current password is wrong, the new passwords differ, or the new one is not accepted
  kind: condition
  entities: []
  contexts:
    web:
      place: web-app::signed-in::security
- text: The Product refuses and keeps the current master password
  kind: product
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Master password set]}
  contexts:
    web:
      place: web-app::signed-in::security
---

# Refuse a master password change

## Trigger

A person makes a mistake changing the password.

## Outcome

Nothing changes.
