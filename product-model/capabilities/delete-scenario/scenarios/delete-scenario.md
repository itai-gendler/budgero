---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a saved scenario
  kind: actor
  actor: user
  entities:
  - {entity: scenario, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::reports
- text: The Product removes the Scenario
  kind: product
  actor: user
  entities:
  - {entity: scenario, effect: removes}
  contexts:
    web:
      place: web-app::signed-in::reports
---

# Delete a scenario

## Trigger

A plan is no longer relevant.

## Outcome

The scenario is gone.
