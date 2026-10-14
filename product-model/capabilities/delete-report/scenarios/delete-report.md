---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a saved report
  kind: actor
  actor: user
  entities:
  - {entity: report, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::explorer
- text: The Product removes the Report
  kind: product
  actor: user
  entities:
  - {entity: report, effect: removes}
  contexts:
    web:
      place: web-app::signed-in::explorer
---

# Delete a report

## Trigger

A report is obsolete.

## Outcome

The report is gone from the list.
