---
kind: primary
routes:
  push: Push API to a member's app
steps:
- text: The Push client sends an encrypted add-transaction operation with the budget, account, category, date and amount, and a message id
  kind: actor
  actor: push-client
  entities:
  - {entity: budget, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  - {entity: account, effect: reads, facts: []}
  - {entity: transaction, effect: reads, facts: []}
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
- text: The Product decrypts the operation and records the Transaction, remembering the message id it came with
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount]}
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

# Push a transaction

## Trigger

A script reads a bank alert email and pushes the expense.

## Outcome

The transaction is in the account once a member's app has processed the queue; continuous rules run on it like on any new transaction.

## Edge cases

- Marking the push as cleared records the transaction cleared.
- Split lines must add up to the total, or the message fails when applied.
