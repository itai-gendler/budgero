---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses to generate a Push API token
  kind: actor
  actor: user
  entities:
  - {entity: push-token, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::push-api
- text: The Product creates an enabled Push API token for the User's default workspace and shows it once
  kind: product
  actor: user
  entities:
  - {entity: push-token, effect: creates, facts: [Enabled, Created at, Last used, Workspace]}
  - {entity: workspace, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::push-api
---

# Generate a push token

## Trigger

A person sets up a script that pushes transactions.

## Outcome

The person copies the token; afterwards only its status is shown.
