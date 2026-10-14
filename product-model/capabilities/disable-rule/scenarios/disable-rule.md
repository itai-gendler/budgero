---
kind: primary
routes:
  web: Web
steps:
- text: The User switches a rule off
  kind: actor
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: The Product pauses the Rule
  kind: product
  actor: user
  entities:
  - {entity: rule, effect: changes, facts: [Enabled]}
  contexts:
    web:
      place: web-app::signed-in::rules
---

# Disable a rule

## Trigger

A rule misbehaves and needs a pause.

## Outcome

The rule neither runs on new transactions nor suggests values.
