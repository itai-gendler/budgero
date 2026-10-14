---
kind: primary
routes:
  web: Web
steps:
- text: The User chooses Periodic Allocation Target or Periodic Available Target, an amount per cycle, a cadence and a start date
  kind: actor
  actor: user
  entities: []
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product creates the Goal with the target date at the end of the first cycle
  kind: product
  actor: user
  entities:
  - {entity: goal, effect: creates, facts: [Target type, Target amount, Start date, Target date, Repeats]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product spreads each cycle's amount evenly across the cycle's months
  kind: condition
  entities:
  - {entity: goal, effect: reads, facts: [Needed this month]}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Create a periodic target

## Trigger

A person plans for a rhythm rather than a date, such as a quarterly tax instalment.

## Outcome

The goal asks for its per-cycle amount spread evenly, cycle after cycle.

## Edge cases

- Cycle end dates keep the start day of the month, clamped in shorter months.
- An available target carries the balance across cycles; an allocation target counts only what is assigned inside the current cycle.
