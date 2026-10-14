---
kind: primary
routes:
  web: Web
steps:
- text: The User renames a dashboard
  kind: actor
  actor: user
  entities:
  - {entity: dashboard, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::custom-dashboards
- text: The Product saves the Dashboard's name
  kind: product
  actor: user
  entities:
  - {entity: dashboard, effect: changes, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::custom-dashboards
---

# Rename a dashboard

## Trigger

A dashboard's purpose changed.

## Outcome

The dashboard shows the new name.
