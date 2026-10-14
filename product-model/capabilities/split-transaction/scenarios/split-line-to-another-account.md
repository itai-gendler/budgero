---
kind: edge
routes:
  web: Web
steps:
- text: The User adds a split line whose target is another account
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product saves the split lines
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: split-transaction, effect: changes, facts: [Split lines]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records a mirrored Transaction in the other account in the Transfers category
  kind: product
  actor: user
  entities:
  - {entity: transaction, as: mirror, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Memo, Payee, Category, Converted amount, Transfer link]}
  - {entity: category, effect: reads, facts: []}
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Split a line off to another account

## Trigger

Part of a paycheck goes straight to savings.

## Outcome

The other account shows its part as a transfer in.
