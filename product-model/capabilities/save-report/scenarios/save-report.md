---
kind: primary
routes:
  web: Web
steps:
- text: The User saves the current query and charts under a name
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::explorer
- text: The Product saves the Report
  kind: product
  actor: user
  entities:
  - {entity: report, effect: creates, facts: [Name, Description, Query, Charts, Favorite]}
  contexts:
    web:
      place: web-app::signed-in::explorer
---

# Save a report

## Trigger

A person wants to rerun a query monthly.

## Outcome

The report is listed and its charts can be pinned to dashboards.

## Edge cases

- A name already used by another report is refused.
