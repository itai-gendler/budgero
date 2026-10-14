---
kind: primary
routes:
  web: Web
steps:
- text: The User asks to process pending pushes from the Push API settings
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::push-api
- text: The Product applies each pending Push message and reports how many were processed and failed
  kind: product
  actor: user
  entities:
  - {entity: push-message, effect: changes, from: Pending, to: Processed, facts: []}
  - {entity: report, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::push-api
---

# Process the push queue on demand

## Trigger

A person wants to see a push land right away.

## Outcome

The queue counts show the messages as processed.
