---
kind: primary
routes:
  web: Web
steps:
- text: The User picks how many days to keep cached rates and whether offline rates update when back online
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::currencies
- text: The Product saves the settings for the Workspace and prunes cached rates older than the new period
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::currencies
---

# Change the rate cache settings

## Trigger

A person budgets offline for long stretches.

## Outcome

Rates stay available offline for the chosen period.
