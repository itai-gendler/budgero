---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a rule
  kind: actor
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: It has no name, no condition or no action, or an action lacks its value
  kind: condition
  entities: []
  contexts:
    web:
      place: web-app::signed-in::rules
- text: The Product refuses and names what is missing
  kind: product
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::rules
---

# Refuse an incomplete rule

## Trigger

A person saves a half-written rule.

## Outcome

No rule is created.

## Edge cases

- Amount conditions need a number.
- Memo conditions cannot be empty.
