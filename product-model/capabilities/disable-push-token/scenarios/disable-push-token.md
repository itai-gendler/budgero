---
kind: primary
routes:
  web: Web
steps:
- text: The User switches the Push API token off
  kind: actor
  actor: user
  entities:
  - {entity: push-token, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::push-api
- text: The Product refuses pushes with the Push API token until it is switched on
  kind: product
  actor: user
  entities:
  - {entity: push-token, effect: changes, facts: [Enabled]}
  contexts:
    web:
      place: web-app::signed-in::push-api
---

# Disable the push token

## Trigger

A person pauses an integration.

## Outcome

Pushes are refused as disabled; the token is kept.
