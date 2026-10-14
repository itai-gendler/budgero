---
kind: validation
routes:
  web: Web
steps:
- text: The User tries to undo a run that is not the rule's most recent completed one
  kind: actor
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: The Product refuses because only the most recent completed run can be undone
  kind: product
  actor: user
  entities:
  - {entity: rule-run, effect: reads, facts: [Trigger]}
  contexts:
    web:
      place: web-app::signed-in::rules
---

# Refuse undoing an older run

## Trigger

A person tries to undo an earlier run.

## Outcome

Nothing changes.
