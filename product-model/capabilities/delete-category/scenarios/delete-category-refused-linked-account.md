---
kind: validation
routes:
  web: Web
steps:
- text: The User deletes a credit card payment category or a loan's linked category
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: Its linked Account is not archived
  kind: condition
  entities:
  - {entity: category, effect: reads, facts: [Linked account]}
  - {entity: account, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product refuses and says to archive or delete the Account first
  kind: product
  actor: user
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Refuse deleting a category an active account depends on

## Trigger

A person tries to delete the category that tracks an active debt account's payments.

## Outcome

The category stays.
