---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Reduce Overfunding from the Assign menu
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product finds goal categories funded past their target for the month
  kind: product
  actor: user
  entities:
  - {entity: goal, effect: reads, facts: [Target amount, Status]}
  - {entity: category, effect: reads, facts: [Available]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product lowers each Assignment by the excess, never below zero assigned or zero available
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: changes, facts: [Amount]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: Ready to Assign rises by the total freed
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Reduce overfunded goal categories

## Trigger

Goals drifted past their targets and the money could work elsewhere.

## Outcome

The excess is back in Ready to Assign for redeployment.
