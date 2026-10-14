---
kind: edge
routes:
  web: Web
steps:
- text: The User enters a transaction dated in the future
  kind: actor
  actor: user
  entities:
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product records the Transaction as scheduled
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: creates, to: Uncleared, facts: [Date, Inflow, Outflow, Payee, Memo, Category, Converted amount]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Account's balance leaves it out until its date
  kind: condition
  entities:
  - {entity: account, effect: reads, facts: [Balance]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Add a future-dated transaction

## Trigger

A person knows about a one-off payment next month.

## Outcome

The entry is in the register and on the upcoming list, but not yet in the realized balance.
