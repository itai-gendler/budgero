---
kind: edge
routes:
  web: Web
steps:
- text: The User chooses Regenerate Token and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::push-api
- text: The Product replaces the Push API token with a new one
  kind: product
  actor: user
  entities:
  - {entity: push-token, effect: changes, facts: [Created at, Enabled]}
  contexts:
    web:
      place: web-app::signed-in::push-api
---

# Regenerate a push token

## Trigger

A token may have leaked.

## Outcome

The old token stops working at once; push clients need the new one.
