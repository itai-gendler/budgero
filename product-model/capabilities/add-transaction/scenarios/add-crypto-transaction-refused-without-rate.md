---
kind: validation
routes:
  web: Web
steps:
- text: The User enters a transaction in a cryptocurrency account
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: No exchange rate to the display currency is known for the date
  kind: condition
  entities:
  - {entity: account, effect: reads, facts: [Currency]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product refuses and asks for a manual rate or a reconnection
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::account
---

# Refuse a crypto amount without an exchange rate

## Trigger

A person records a crypto movement while offline with no cached rate.

## Outcome

No transaction is recorded.
