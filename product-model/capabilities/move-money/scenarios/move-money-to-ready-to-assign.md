---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Move Money on a category and picks Ready to Assign as the target
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product lowers the category's Assignment for the month by the amount, capped at its Available
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: changes, facts: [Amount]}
  - {entity: category, effect: reads, facts: [Available]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: Ready to Assign rises by the amount
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Return money to Ready to Assign

## Trigger

A person frees money a category no longer needs.

## Outcome

The money has no job again and can be assigned elsewhere.
