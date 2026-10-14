---
kind: primary
routes:
  web: Web
steps:
- text: The User clears the audit log and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::audit-log
- text: The Product removes every Audit log entry; the budget is unchanged
  kind: product
  actor: user
  entities:
  - {entity: audit-log-entry, effect: removes, from: Applied}
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::audit-log
---

# Clear the audit log

## Trigger

A person wants a clean history.

## Outcome

The audit log is empty.
