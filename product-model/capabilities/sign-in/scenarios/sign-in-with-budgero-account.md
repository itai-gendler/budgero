---
kind: primary
routes:
  web: Web
steps:
- text: The Visitor signs in with their Budgero Cloud login
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web-app::signed-out::sign-in
- text: The Product opens a session for the User and loads the workspaces they belong to
  kind: product
  entities:
  - {entity: user, effect: reads, facts: [Email, Master password set]}
  - {entity: workspace, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-out::sign-in
---

# Sign in with a Budgero Cloud account

## Trigger

A person opens the hosted Budgero.

## Outcome

They are signed in and move on to unlocking their data.
