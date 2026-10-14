---
kind: validation
routes:
  web: Web
steps:
- text: The User enters a master password and its confirmation
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: A strength rule is unmet or the confirmation differs
  kind: condition
  entities:
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::master-password
- text: The Product keeps Set Master Password unavailable and shows which rules are unmet
  kind: product
  actor: user
  entities:
  - {entity: user, effect: reads, facts: [Master password set]}
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::master-password
---

# Refuse a weak or mismatched master password

## Trigger

A person picks a short or simple password.

## Outcome

No master password is set until every rule is met.
