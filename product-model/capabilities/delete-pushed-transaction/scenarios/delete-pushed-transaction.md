---
kind: primary
routes:
  push: Push API to a member's app
steps:
- text: The Push client sends an encrypted delete operation naming the original message id
  kind: actor
  actor: push-client
  entities: []
  contexts:
    push:
      place: push-api
- text: The Product checks the token and queues the encrypted operation as a pending Push message
  kind: product
  entities:
  - {entity: push-message, effect: creates, to: Pending, facts: [Message id, Received at, Operation]}
  - {entity: push-token, effect: reads, facts: [Enabled]}
  contexts:
    push:
      place: push-api
- text: A member of the workspace opens it in the app, which applies pending messages
  kind: condition
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    push:
      place: web-app::signed-in
- text: The Product deletes the Transaction that push added
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: removes, from: Uncleared}
  contexts:
    push:
      place: web-app::signed-in
- text: The Product marks the Push message processed
  kind: product
  actor: user
  entities:
  - {entity: push-message, effect: changes, from: Pending, to: Processed, facts: []}
  contexts:
    push:
      place: web-app::signed-in
---

# Delete a pushed transaction

## Trigger

A bank reverses a charge the script had pushed.

## Outcome

The transaction is gone.

## Edge cases

- If the transaction is already gone the message still counts as processed.
