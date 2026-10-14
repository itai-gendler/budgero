---
kind: validation
routes:
  web: Web
steps:
- text: The Visitor tries to register
  kind: actor
  actor: visitor
  entities: []
  contexts:
    web:
      place: web-app::signed-out::sign-in
- text: The instance has registration disabled
  kind: condition
  entities: []
  contexts:
    web:
      place: web-app::signed-out::sign-in
- text: The Product refuses the registration
  kind: product
  entities: []
  contexts:
    web:
      place: web-app::signed-out::sign-in
---

# Refuse sign-up while registration is disabled

## Trigger

An operator closed registration on their instance.

## Outcome

No account is created.

## Edge cases

- A username already taken is refused with the same generic message.
