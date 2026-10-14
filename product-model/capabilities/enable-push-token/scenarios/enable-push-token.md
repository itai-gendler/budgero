---
kind: primary
routes:
  web: Web
steps:
- text: The User switches the Push API token on
  kind: actor
  actor: user
  entities:
  - {entity: push-token, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::push-api
- text: The Product accepts pushes with the Push API token again
  kind: product
  actor: user
  entities:
  - {entity: push-token, effect: changes, facts: [Enabled]}
  contexts:
    web:
      place: web-app::signed-in::push-api
---

# Enable the push token

## Trigger

A person resumes their integration.

## Outcome

Pushes are accepted again.
