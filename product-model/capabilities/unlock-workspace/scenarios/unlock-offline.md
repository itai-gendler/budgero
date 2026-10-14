---
kind: edge
routes:
  web: Web
steps:
- text: The device has no connection to the server
  kind: condition
  entities: []
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The User enters their master password and chooses Unlock
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The Product decrypts the data kept on the device and opens the Workspace offline
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::master-password
---

# Unlock while offline

## Trigger

A person opens Budgero on a plane.

## Outcome

They budget offline; changes synchronise when the device reconnects.
