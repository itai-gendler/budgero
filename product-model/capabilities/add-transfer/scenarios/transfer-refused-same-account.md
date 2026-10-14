---
kind: validation
routes:
  web: Web
steps:
- text: The User enters a transfer whose source and destination are the same account
  kind: actor
  actor: user
  entities:
  - {entity: account, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product refuses because the accounts must differ
  kind: product
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Refuse a transfer to the same account

## Trigger

A person picks the same account twice.

## Outcome

No transaction is recorded.
