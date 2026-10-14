---
kind: primary
result: achieved
routes:
  web: Web
steps:
- text: The User resets Budgero
  kind: actor
  actor: user
  capability: reset-master-password
  entities:
  - {entity: user, effect: changes, facts: [Master password set]}
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The Product reloads and carries the User to creating a master password
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The User sets a new master password
  kind: actor
  actor: user
  capability: set-master-password
  entities:
  - {entity: user, effect: changes, facts: [Master password set]}
  contexts:
    web:
      place: web-app::signed-in::master-password
---

# Reset and set a new master password

## Trigger

A person has forgotten their master password.

## Outcome

They are back in Budgero with a fresh master password and no former data.
