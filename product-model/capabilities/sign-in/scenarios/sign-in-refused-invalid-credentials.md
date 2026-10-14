---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor enters a username and password on a self-hosted instance
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web-app::signed-out::sign-in
- text: They do not match an account
  kind: condition
  entities:
  - {entity: account, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-out::sign-in
- text: The Product refuses with a generic invalid-credentials message
  kind: product
  entities: []
  contexts:
    web:
      place: web-app::signed-out::sign-in
---

# Refuse invalid local credentials

## Trigger

A person mistypes their password.

## Outcome

No session is opened.
