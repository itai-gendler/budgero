---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Reveal Key and confirms the security warning
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::push-api
- text: The Product shows the Workspace key from the device and hides it again after 60 seconds
  kind: product
  actor: user
  entities:
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::push-api
---

# Reveal the workspace encryption key

## Trigger

A person configures the Python SDK.

## Outcome

The person copies the key; anyone holding it can read the workspace's data.
