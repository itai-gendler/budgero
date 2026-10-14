---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Move Money, an amount and a target
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product caps the amount at the source category's Available
  kind: product
  actor: user
  entities:
  - {entity: category, as: source, effect: reads, facts: [Available]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product lowers the source category's Assignment and raises the target category's Assignment for the month in one change
  kind: product
  actor: user
  entities:
  - {entity: assignment, as: source-assignment, effect: changes, facts: [Amount]}
  - {entity: assignment, as: target-assignment, effect: changes, facts: [Amount]}
  - {entity: category, as: target, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Move money to another category

## Trigger

A person needs money in one category and decides which other category gives it up.

## Outcome

Available falls in the source and rises in the target by the moved amount; Ready to Assign is unchanged.

## Edge cases

- If lowering the source would overspend a future month, the future overspending warning appears first.
