---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Monthly Available Target for a category and enters the amount
  kind: actor
  actor: user
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product creates the Goal starting this month
  kind: product
  actor: user
  entities:
  - {entity: goal, effect: creates, facts: [Target type, Target amount, Start date, Repeats]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product shows what the category needs this month and the goal's status
  kind: condition
  entities:
  - {entity: goal, effect: reads, facts: [Needed this month, Status]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Create a monthly available target

## Trigger

A person wants a category to start each month with a set amount available, such as groceries.

## Outcome

The category has a goal and shows how much it still needs this month.
