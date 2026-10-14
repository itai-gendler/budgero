---
kind: edge
routes:
  web: Web
steps:
- text: The User chooses Cover Overspending
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: Ready to Assign is smaller than the total overspending
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  - {entity: category, effect: reads, facts: [Available]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product covers the largest overspending first and stops when Ready to Assign is used up
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: changes, facts: [Amount]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Cover overspending only as far as Ready to Assign goes

## Trigger

Overspending exceeds the money without a job.

## Outcome

Ready to Assign reaches zero; the smallest overspent categories stay negative.
