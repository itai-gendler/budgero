---
kind: primary
routes:
  web: Web
steps:
- text: The User picks a saved report's chart and a dashboard, with an optional title
  kind: actor
  actor: user
  entities:
  - {entity: report, effect: reads, facts: [Name, Charts]}
  - {entity: dashboard, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::custom-dashboards
- text: The Product adds the Widget to the Dashboard
  kind: product
  actor: user
  entities:
  - {entity: widget, effect: creates, facts: [Chart, Title, Position]}
  - {entity: dashboard, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::custom-dashboards
---

# Pin a chart to a dashboard

## Trigger

A person wants a chart always in view.

## Outcome

The chart shows on the dashboard with live data.
