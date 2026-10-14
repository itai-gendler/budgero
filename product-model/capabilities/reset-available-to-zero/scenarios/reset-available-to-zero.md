---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Reset Available to Zero from the Assign menu and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product sets each category's Assignment to its current assignment minus its Available
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: [Available]}
  - {entity: assignment, effect: changes, facts: [Amount]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product reports how many categories changed and the net change
  kind: condition
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  - {entity: report, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Reset every Available to zero

## Trigger

A person restructures a month and wants every envelope empty.

## Outcome

Every category shows zero Available; Ready to Assign absorbs the net change.

## Edge cases

- When every Available is already zero nothing changes.
