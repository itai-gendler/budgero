---
kind: validation
routes:
  web: Web
steps:
- text: The User chooses Mark ready on an occurrence
  kind: actor
  actor: user
  entities:
  - {entity: occurrence, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
- text: Its template is paused
  kind: condition
  entities:
  - {entity: recurring-transaction, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::account
- text: The Product refuses because the recurring transaction is inactive
  kind: product
  actor: user
  entities:
  - {entity: occurrence, effect: reads, facts: [Due date]}
  - {entity: recurring-transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::account
---

# Refuse posting an occurrence of a paused template

## Trigger

A person tries to post from a paused template.

## Outcome

Nothing is posted.

## Edge cases

- An occurrence that is already posted or skipped cannot be posted again.
