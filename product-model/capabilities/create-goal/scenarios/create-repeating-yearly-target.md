---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Yearly Allocation Target or Yearly Available Target, an amount, a target date and Repeats every year
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product creates the Goal with that date and a twelve-month cycle
  kind: product
  actor: user
  entities:
  - {entity: goal, effect: creates, facts: [Target type, Target amount, Start date, Target date, Repeats]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product spreads the remaining amount over the months left to the target date
  kind: condition
  entities:
  - {entity: goal, effect: reads, facts: [Needed this month]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Create a yearly target that repeats every year

## Trigger

A person saves for a dated expense that comes back every year, such as car registration.

## Outcome

The goal asks for a monthly share and its next cycle starts the month after each target date.
