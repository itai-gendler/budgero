---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a category that has transactions
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product asks for a destination category to receive its data
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The User picks a different category and confirms
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product moves every Transaction and Assignment of the category to the destination
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: changes, facts: [Category]}
  - {entity: assignment, effect: changes, facts: [Category]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product deletes the Category
  kind: product
  actor: user
  entities:
  - {entity: category, effect: removes}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Delete a category and move its history to another

## Trigger

A person consolidates two categories.

## Outcome

All transactions and assignments now belong to the destination category and the deleted category is gone.

## Edge cases

- Picking the same category as the destination is refused.
- An income category's history can only move to another income category.
