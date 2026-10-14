---
kind: edge
routes:
  web: Web
steps:
- text: A member's app has opened the workspace and caught up with sync while push messages are pending
  kind: condition
  unattended: true
  entities:
  - {entity: push-message, effect: reads, facts: [Operation]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product decrypts each Push message on the device and applies its operation
  kind: product
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  - {entity: push-message, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in
- text: The Product marks each applied Push message processed
  kind: product
  entities:
  - {entity: push-message, effect: changes, from: Pending, to: Processed, facts: []}
  contexts:
    web:
      place: web-app::signed-in
---

# Process the push queue when the workspace opens

## Trigger

A member opens the app after pushes arrived.

## Outcome

Pushed changes appear in the budget on every member's devices.
