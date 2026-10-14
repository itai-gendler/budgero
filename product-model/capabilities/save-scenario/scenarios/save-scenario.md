---
kind: primary
routes:
  web: Web
steps:
- text: The User sets a forecast model, income and spending changes, horizon and one-off events and saves them under a name
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::reports
- text: The Product saves the Scenario for the budget
  kind: product
  actor: user
  entities:
  - {entity: scenario, effect: creates, facts: [Name, Forecast model, Income change, Spending change, Horizon, One-off events]}
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::reports
---

# Save a scenario

## Trigger

A person models a pay rise and a new car.

## Outcome

The scenario can be reopened and compared later.
