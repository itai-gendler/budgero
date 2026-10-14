---
kind: edge
routes:
  web: Web
steps:
- text: A pending message does not decrypt with the workspace key, is not a valid operation, uses a newer data format, or its operation is refused
  kind: condition
  unattended: true
  entities:
  - {entity: push-message, effect: reads, facts: [Operation]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product marks the Push message failed and records the error in the audit log
  kind: product
  entities:
  - {entity: push-message, effect: changes, from: Pending, to: Failed, facts: []}
  contexts:
    web:
      place: web-app::signed-in
---

# Fail a push message that cannot be applied

## Trigger

A push client encrypted with the wrong key or sent an invalid operation.

## Outcome

Nothing changes in the budget; the failure is visible in the queue counts and the audit log.

## Edge cases

- A message from a newer data format also asks the person to update the app.
