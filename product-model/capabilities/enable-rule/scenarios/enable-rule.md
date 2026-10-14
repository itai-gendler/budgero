---
kind: primary
routes:
  web: Web
steps:
- text: The User switches a rule on
  kind: actor
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: The Product enables the Rule
  kind: product
  actor: user
  entities:
  - {entity: rule, effect: changes, facts: [Enabled]}
  contexts:
    web:
      place: web-app::signed-in::rules
---

# Enable a rule

## Trigger

A paused rule is wanted again.

## Outcome

The rule runs and suggests again.
