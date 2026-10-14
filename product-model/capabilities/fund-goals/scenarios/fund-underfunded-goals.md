---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Fund Goals from the Assign menu
  kind: actor
  actor: user
  entities:
  - {entity: goal, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product works out what each goal still needs this month
  kind: product
  actor: user
  entities:
  - {entity: goal, effect: reads, facts: [Needed this month, Status]}
  - {entity: category, effect: reads, facts: [Funding priority]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product funds whole priority tiers in order while positive Ready to Assign lasts
  kind: product
  actor: user
  entities:
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product raises the Assignment of each funded category in one batch
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: changes, facts: [Amount]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product reports the total assigned and the categories it funded
  kind: condition
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  - {entity: report, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Fund every underfunded goal

## Trigger

Income has arrived and a person wants every goal funded before distributing the rest by hand.

## Outcome

Every goal Ready to Assign could cover is funded for the month, and Ready to Assign is lower by the total.

## Edge cases

- With no underfunded goals the Product says all goals are fully funded and changes nothing.
- Yearly, repeating and target-date goals are funded only up to this month's milestone.
