---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Proportional shortfalls or Equal completion percentage
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget-settings
- text: The Product saves the Budget's sharing setting for later goal funding
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: changes, facts: [Sharing within a priority, Show priority badges]}
  - {entity: goal, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget-settings
---

# Change how limited money is shared

## Trigger

A person wants a different fairness rule when goals of one priority compete for money.

## Outcome

The next Fund Goals shares limited money the chosen way; existing assignments are unchanged.
