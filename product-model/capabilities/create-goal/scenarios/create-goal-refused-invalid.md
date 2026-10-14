---
kind: validation
routes:
  web: Web
steps:
- text: The User saves a goal
  kind: actor
  actor: user
  entities:
  - {entity: goal, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The amount is not above zero, a yearly target lacks a date or its date is not after the start, or a cadence is outside 2 to 120 months
  kind: condition
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product lists the problems and creates no Goal
  kind: product
  actor: user
  entities:
  - {entity: category, effect: reads, facts: [Name]}
  - {entity: goal, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Refuse an invalid goal

## Trigger

A person fills the goal form incompletely or inconsistently.

## Outcome

The category keeps no goal until the form is valid.
