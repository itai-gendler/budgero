---
kind: validation
routes:
  api: Push API
steps:
- text: The Push client resends an operation with a message id it used before
  kind: actor
  actor: push-client
  entities: []
  contexts:
    api:
      place: push-api
- text: A Push message with that id already exists in the workspace
  kind: condition
  entities:
  - {entity: push-message, effect: reads, facts: [Message id]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    api:
      place: push-api
- text: The Product answers that the message is a duplicate and queues nothing
  kind: product
  entities: []
  contexts:
    api:
      place: push-api
---

# Refuse a retried push with a known message id

## Trigger

A push client retries after a network timeout.

## Outcome

The transaction is not added twice.
