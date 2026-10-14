---
kind: validation
routes:
  api: Push API
steps:
- text: The Push client sends an operation
  kind: actor
  actor: push-client
  entities: []
  contexts:
    api:
      place: push-api
- text: The token is unknown, revoked or disabled
  kind: condition
  entities:
  - {entity: push-token, effect: reads, facts: [Enabled]}
  contexts:
    api:
      place: push-api
- text: The Product refuses the push without queueing anything
  kind: product
  entities: []
  contexts:
    api:
      place: push-api
---

# Refuse a push with an invalid or disabled token

## Trigger

A push client uses an old or disabled token.

## Outcome

Nothing is queued; the client is told the token is invalid or the Push API is disabled.
