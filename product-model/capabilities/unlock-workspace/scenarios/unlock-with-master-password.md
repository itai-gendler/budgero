---
kind: primary
routes:
  web: Web
steps:
- text: The User enters their master password and chooses Unlock
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The Product unwraps the workspace key on the device and opens the Workspace
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::master-password
---

# Unlock with the master password

## Trigger

A person opens Budgero on a device that does not remember the key.

## Outcome

Their budgets are decrypted and ready.

## Edge cases

- On Security settings the key can be remembered on the device for 1 to 30 days instead of memory only.
