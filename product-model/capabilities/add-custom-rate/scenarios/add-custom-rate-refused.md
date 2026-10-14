---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a custom rate
  kind: actor
  actor: user
  entities:
  - {entity: custom-rate, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::currencies
- text: Both currencies are the same, the rate is not positive, or the start date is missing
  kind: condition
  entities: []
  contexts:
    web:
      place: web-app::signed-in::currencies
- text: The Product refuses the Custom rate
  kind: product
  actor: user
  entities:
  - {entity: custom-rate, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::currencies
---

# Refuse an invalid custom rate

## Trigger

A person fills the rate form incorrectly.

## Outcome

No rate is saved.
