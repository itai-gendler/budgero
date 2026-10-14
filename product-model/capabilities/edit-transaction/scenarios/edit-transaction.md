---
kind: primary
routes:
  web: Web
steps:
- text: The User changes a transaction's date, payee, memo, category or amount
  kind: actor
  actor: user
  entities:
  - {entity: payee, effect: reads, facts: []}
  - {entity: category, effect: reads, facts: []}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product saves the Transaction and recalculates the running balances of the Account
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: changes, facts: [Date, Payee, Memo, Category, Inflow, Outflow, Converted amount]}
  - {entity: account, effect: reads, facts: [Balance]}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Edit a transaction

## Trigger

A person corrects an entry.

## Outcome

The register, the account balance and the affected categories reflect the change.
