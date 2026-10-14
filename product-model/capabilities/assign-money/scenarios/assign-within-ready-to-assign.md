---
kind: primary
routes:
  web: Web
steps:
- text: The User types a new Assigned amount for a category in the viewed month
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product compares the increase with Ready to Assign for that month
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign, Ready to Assign mode]}
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product records the Assignment of the category for that month
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: creates, facts: [Month, Amount, Category]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: Ready to Assign drops by the increase and the category's Available rises by it
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  - {entity: category, effect: reads, facts: [Available]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Assign money within Ready to Assign

## Trigger

A person decides how much of the money without a job a category should get this month.

## Outcome

The category holds the new assignment for the month and Ready to Assign is lower by the same amount.

## Edge cases

- Typing an expression such as +25 or *2 applies it to the current Assigned amount.
- Assigning in a future month draws from the same Ready to Assign immediately in Cumulative mode.
