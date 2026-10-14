---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to undo a recent change in the audit log and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::audit-log
- text: The Product reverts the change and marks the Audit log entry undone
  kind: product
  actor: user
  entities:
  - {entity: audit-log-entry, effect: changes, from: Applied, to: Undone, facts: []}
  contexts:
    web:
      place: web-app::signed-in::audit-log
---

# Undo a change from the audit log

## Trigger

A person regrets a change.

## Outcome

The budget is as it was before that change.

## Edge cases

- Changes recorded without an undo, such as synchronised changes from another device, cannot be undone here.
- Several changes made by one action, such as one Fund Goals run, undo together.
