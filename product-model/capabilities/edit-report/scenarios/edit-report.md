---
kind: primary
routes:
  web: Web
steps:
- text: The User changes a saved report and saves
  kind: actor
  actor: user
  entities:
  - {entity: report, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::explorer
- text: The Product saves the Report; dashboards pinning its charts follow
  kind: product
  actor: user
  entities:
  - {entity: report, effect: changes, facts: [Name, Description, Query, Charts]}
  - {entity: dashboard, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::explorer
---

# Edit a report

## Trigger

A report needs another chart.

## Outcome

The report shows the new definition.
