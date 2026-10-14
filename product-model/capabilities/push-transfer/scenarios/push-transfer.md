---
kind: primary
routes:
  push: Push API to a member's app
steps:
- text: The Push client sends an encrypted add-transfer operation with a new transfer id and its source and destination legs
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
- text: The Product records both legs with the shared transfer link
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: source-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
  - {entity: transaction, as: destination-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
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

# Push a transfer

## Trigger

A savings app reports a sweep from checking to savings.

## Outcome

Both accounts show one linked transfer.

## Edge cases

- A transfer id already in use makes the message fail.
