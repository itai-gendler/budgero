---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a dashboard
  kind: actor
  actor: user
  entities:
  - {entity: dashboard, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::custom-dashboards
- text: The Product removes the Dashboard with its Widgets; the saved reports stay
  kind: product
  actor: user
  entities:
  - {entity: dashboard, effect: removes}
  - {entity: widget, effect: removes, with: dashboard}
  - {entity: report, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::custom-dashboards
---

# Delete a dashboard

## Trigger

A dashboard is no longer used.

## Outcome

The dashboard is gone.
