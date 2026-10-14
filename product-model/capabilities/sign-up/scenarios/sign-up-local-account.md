---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters a name, username and a password of at least eight characters
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web-app::signed-out::sign-in
- text: The Product creates the User with no master password yet and signs them in
  kind: product
  entities:
  - {entity: user, effect: creates, facts: [Name, Email, Master password set, Workspace access]}
  contexts:
    web:
      place: web-app::signed-out::sign-in
---

# Register a local account

## Trigger

A household member joins the family's self-hosted instance.

## Outcome

They are signed in and asked to create their master password.
