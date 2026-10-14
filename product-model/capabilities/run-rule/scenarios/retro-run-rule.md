---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Retro run on a rule and confirms
  kind: actor
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: The Product applies the Rule's actions in order to every matching Transaction of the budget
  kind: product
  actor: user
  entities:
  - {entity: rule, effect: reads, facts: [Conditions, Actions]}
  - {entity: transaction, effect: changes, facts: [Payee, Memo, Category, Inflow, Outflow]}
  - {entity: budget, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
- text: The Product records the Rule run with the transactions evaluated and changed
  kind: product
  actor: user
  entities:
  - {entity: rule-run, effect: creates, to: Completed, facts: [Trigger, Evaluated, Changed, Changes, Errors]}
  - {entity: rule, effect: changes, facts: [Consumed]}
  - {entity: transaction, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::rules
---

# Run a rule over past transactions

## Trigger

A person writes a rule they wish they had a year ago.

## Outcome

Past transactions are cleaned up and the result shows how many were evaluated and changed; a One time rule is marked consumed.

## Edge cases

- Retro run is unavailable for a One time rule that is already consumed.
- Transactions the rule could not change are listed as errors while the rest are changed.
