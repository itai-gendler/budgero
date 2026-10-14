---
kind: primary
routes:
  push: Push API to a member's app
steps:
- text: The Push client sends an encrypted delete-transfer operation with the transfer id
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
- text: The Product deletes both legs of the transfer
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: source-leg, effect: removes, from: Uncleared}
  - {entity: transaction, as: destination-leg, effect: removes, from: Uncleared}
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

# Delete a pushed transfer

## Trigger

A pushed transfer turns out to be wrong.

## Outcome

Neither account shows the transfer.
