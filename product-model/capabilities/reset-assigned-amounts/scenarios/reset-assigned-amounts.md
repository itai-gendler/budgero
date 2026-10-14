---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Reset Assigned Amounts from the Assign menu and confirms
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product sets every category's Assignment for the month to zero
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: changes, facts: [Amount]}
  - {entity: category, effect: reads, facts: [Name]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: Ready to Assign rises by everything that had been assigned this month
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Reset every assignment of the month

## Trigger

A person wants to clear the month's plan and assign again from scratch.

## Outcome

Every category shows zero assigned for the month.
