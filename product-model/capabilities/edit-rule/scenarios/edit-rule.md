---
kind: primary
routes:
  web: Web
steps:
- text: The User edits a rule and saves
  kind: actor
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: The Product saves the Rule
  kind: product
  actor: user
  entities:
  - {entity: rule, effect: changes, facts: [Name, Mode, Conditions, Actions, Run order]}
  contexts:
    web:
      place: web-app::signed-in::rules
---

# Edit a rule

## Trigger

A rule matched too much.

## Outcome

Later runs use the new definition; earlier changes stay.
