---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes an account with no transactions and a zero balance
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product deletes the Account and the payment or linked Category it owned
  kind: product
  actor: user
  entities:
  - {entity: account, effect: removes, from: Open}
  - {entity: category, effect: removes}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product returns to the home page
  kind: condition
  entities: []
  contexts:
    web:
      place: web-app::signed-in
---

# Delete an empty account

## Trigger

A person added an account by mistake.

## Outcome

The account is gone permanently.
