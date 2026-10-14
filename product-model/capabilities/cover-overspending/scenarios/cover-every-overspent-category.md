---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Cover Overspending from the Assign menu
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product lists the categories whose Available is negative, largest first
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: [Available, Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product raises each one's Assignment by its overspending while Ready to Assign lasts
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: changes, facts: [Amount]}
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Cover every overspent category

## Trigger

Categories went negative and Ready to Assign has enough to cover them.

## Outcome

Every overspent category is back to zero Available and Ready to Assign is lower by the total.

## Edge cases

- The action is unavailable while Ready to Assign is zero or negative and over-assignment is off.
