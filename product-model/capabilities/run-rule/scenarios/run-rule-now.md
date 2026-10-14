---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Run now on a rule
  kind: actor
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: The Product applies the Rule to every matching Transaction and records the Rule run
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: changes, facts: [Payee, Memo, Category]}
  - {entity: rule-run, effect: creates, to: Completed, facts: [Trigger, Evaluated, Changed, Changes, Errors]}
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
---

# Run a rule now

## Trigger

A person wants a rule applied immediately.

## Outcome

The run appears in the rule's history.
