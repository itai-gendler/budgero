---
kind: validation
routes:
  web: Web
steps:
- text: Ready to Assign is zero or negative and over-assignment is off
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  - {entity: workspace, effect: reads, facts: [Allow over-assignment]}
  - {entity: assignment, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The User opens the Assign menu
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product shows Fund Goals as unavailable
  kind: product
  actor: user
  entities:
  - {entity: goal, effect: reads, facts: [Needed this month, Status]}
  - {entity: category, effect: reads, facts: [Funding priority]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Fund Goals is unavailable without money to assign

## Trigger

A person has nothing left to assign.

## Outcome

No goal is funded; only reducing overfunding remains offered.
