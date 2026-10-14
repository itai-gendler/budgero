---
kind: primary
routes:
  web: Web
steps:
- text: The User picks Monthly or Cumulative as the Ready to Assign mode
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget-settings
- text: The Product saves the Budget's mode and recalculates Ready to Assign and category balances
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: changes, facts: [Ready to Assign mode]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget-settings
- text: Ready to Assign follows the chosen mode
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in::budget-settings
---

# Switch the Ready to Assign mode

## Trigger

A person coming from YNAB wants each month to stand on its own, or prefers one continuous pool.

## Outcome

Ready to Assign and Available follow the chosen mode; no transaction or assignment changed.
