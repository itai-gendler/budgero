---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a recurring transaction
  kind: actor
  actor: user
  entities:
  - {entity: recurring-transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The end date is before the start date, the amount is invalid, or a transfer uses the same account twice
  kind: condition
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
- text: The Product refuses and keeps the form open
  kind: product
  actor: user
  entities:
  - {entity: recurring-transaction, effect: reads, facts: [Schedule]}
  contexts:
    web:
      place: web-app::signed-in::recurring-transactions
---

# Refuse an invalid recurring transaction

## Trigger

A person fills the template inconsistently.

## Outcome

No template is saved.
