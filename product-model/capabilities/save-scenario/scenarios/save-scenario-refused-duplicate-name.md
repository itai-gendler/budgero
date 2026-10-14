---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a scenario
  kind: actor
  actor: user
  entities:
  - {entity: scenario, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::reports
- text: Another scenario of the budget has that name
  kind: condition
  entities:
  - {entity: scenario, effect: reads, facts: [Name]}
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::reports
- text: The Product refuses the name
  kind: product
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::reports
---

# Refuse a duplicate scenario name

## Trigger

A person reuses a scenario name.

## Outcome

Nothing is saved under the duplicate name.
