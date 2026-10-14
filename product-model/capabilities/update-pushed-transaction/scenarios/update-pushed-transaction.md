---
kind: primary
routes:
  push: Push API to a member's app
steps:
- text: The Push client sends an encrypted update operation naming the original message id and the new values
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
- text: The Product finds the Transaction that push added and applies all the new values together
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: changes, facts: [Date, Inflow, Outflow, Payee, Memo, Category]}
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

# Update a pushed transaction

## Trigger

A pending card charge settles at a different amount.

## Outcome

The transaction shows the corrected values.

## Edge cases

- A transfer cannot be updated this way, and a split transaction accepts only memo, payee and cleared changes.
- A reconciled transaction keeps its cleared status.
- Unknown fields make the message fail.
