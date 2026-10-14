---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Revoke Token and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::push-api
- text: The Product deletes the Push API token
  kind: product
  actor: user
  entities:
  - {entity: push-token, effect: removes}
  contexts:
    web:
      place: web-app::signed-in::push-api
---

# Revoke the push token

## Trigger

A person stops using the Push API.

## Outcome

Every push with the old token is refused.
