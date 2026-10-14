---
kind: primary
routes:
  web: Web
steps:
- text: The User opens a rule's history and undoes its latest run
  kind: actor
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: The Product restores every Transaction the run changed and marks the Rule run undone
  kind: product
  actor: user
  entities:
  - {entity: transaction, effect: changes, facts: [Payee, Memo, Category, Inflow, Outflow]}
  - {entity: rule-run, effect: changes, from: Completed, to: Undone, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: A One time rule can run again
  kind: condition
  entities:
  - {entity: rule, effect: reads, facts: [Consumed]}
  contexts:
    web:
      place: web-app::signed-in::rules
---

# Undo a rule's latest run

## Trigger

A retro run grabbed more than intended.

## Outcome

The transactions are as they were before the run.
