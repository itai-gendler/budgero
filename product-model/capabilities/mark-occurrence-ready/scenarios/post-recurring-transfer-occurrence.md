---
kind: primary
routes:
  settings: Recurring Transactions page
  register: Account register upcoming panel
steps:
- text: The User chooses Mark ready on an occurrence of a recurring transfer
  kind: actor
  actor: user
  entities:
  - {entity: occurrence, effect: reads, facts: []}
  contexts:
    settings:
      place: web-app::signed-in::recurring-transactions
    register:
      place: web-app::signed-in::account
- text: The Product records the two linked legs, converting the amount for a destination in another currency
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: source-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
  - {entity: transaction, as: destination-leg, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount, Transfer link]}
  - {entity: recurring-transaction, effect: reads, facts: [Transfer destination]}
  contexts:
    settings:
      place: web-app::signed-in::recurring-transactions
    register:
      place: web-app::signed-in::account
- text: The Product marks the Occurrence ready
  kind: product
  actor: user
  entities:
  - {entity: occurrence, effect: changes, from: Scheduled, to: Ready, facts: []}
  contexts:
    settings:
      place: web-app::signed-in::recurring-transactions
    register:
      place: web-app::signed-in::account
---

# Post a recurring transfer occurrence

## Trigger

Payday arrives and the savings transfer is confirmed.

## Outcome

Both accounts show the transfer.

## Edge cases

- If the second leg cannot be recorded the first is removed and the occurrence stays scheduled.
