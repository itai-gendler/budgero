---
kind: primary
routes:
  web: Web
steps:
- text: The User creates a dashboard with a name
  kind: actor
  actor: user
  entities:
  - {entity: dashboard, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::custom-dashboards
- text: The Product saves the Dashboard
  kind: product
  actor: user
  entities:
  - {entity: dashboard, effect: creates, facts: [Name, Position]}
  contexts:
    web:
      place: web-app::signed-in::custom-dashboards
---

# Create a dashboard

## Trigger

A person wants their key charts on one page.

## Outcome

An empty dashboard is ready for charts.

## Edge cases

- A name already used by another dashboard of the budget, ignoring case, is refused.
