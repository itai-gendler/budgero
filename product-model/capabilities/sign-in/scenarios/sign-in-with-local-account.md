---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor enters their username and password on the self-hosted instance
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web-app::signed-out::sign-in
- text: The Product checks the credentials and opens a session for the User
  kind: product
  entities:
  - {entity: user, effect: reads, facts: [Email, Master password set]}
  contexts:
    web:
      place: web-app::signed-out::sign-in
---

# Sign in with a local account

## Trigger

A person opens their household's self-hosted Budgero.

## Outcome

They are signed in to that instance.
