---
kind: primary
routes:
  web: Web
steps:
- text: The User removes a chart from a dashboard
  kind: actor
  actor: user
  entities:
  - {entity: dashboard, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::custom-dashboards
- text: The Product removes the Widget; the saved report keeps the chart
  kind: product
  actor: user
  entities:
  - {entity: widget, effect: removes}
  - {entity: report, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::custom-dashboards
---

# Remove a chart from a dashboard

## Trigger

A chart is no longer useful on the dashboard.

## Outcome

The dashboard no longer shows it.
