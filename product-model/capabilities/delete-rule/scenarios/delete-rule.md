---
kind: primary
routes:
  web: Web
steps:
- text: The User deletes a rule and confirms
  kind: actor
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: The Product removes the Rule with its run history
  kind: product
  actor: user
  entities:
  - {entity: rule, effect: removes}
  - {entity: rule-run, effect: removes, from: Completed, with: rule}
  contexts:
    web:
      place: web-app::signed-in::rules
---

# Delete a rule

## Trigger

A rule is no longer needed.

## Outcome

The rule never runs again; transactions it changed keep their values.
