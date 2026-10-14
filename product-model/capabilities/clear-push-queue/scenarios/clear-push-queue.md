---
kind: primary
routes:
  web: Web
steps:
- text: The User clears the push queue
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::push-api
- text: The Product deletes every pending Push message
  kind: product
  actor: user
  entities:
  - {entity: push-message, effect: removes, from: Pending}
  contexts:
    web:
      place: web-app::signed-in::push-api
---

# Clear the push queue

## Trigger

A misconfigured script queued junk.

## Outcome

The pending count is zero and nothing was applied.
