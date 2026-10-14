---
kind: edge
routes:
  web: Web
steps:
- text: The User chooses Fund Goals
  kind: actor
  actor: user
  entities:
  - {entity: goal, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product fully funds the tiers Ready to Assign covers
  kind: product
  actor: user
  entities:
  - {entity: goal, effect: reads, facts: [Needed this month, Status]}
  - {entity: category, effect: reads, facts: [Funding priority]}
  - {entity: budget, effect: reads, facts: [Ready to Assign]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The money runs out inside one priority tier
  kind: condition
  entities:
  - {entity: budget, effect: reads, facts: [Sharing within a priority]}
  contexts:
    web:
      place: web-app::signed-in::budget
- text: The Product shares the remaining money among that tier's categories and raises their Assignments
  kind: product
  actor: user
  entities:
  - {entity: assignment, effect: changes, facts: [Amount]}
  - {entity: category, effect: reads, facts: []}
  contexts:
    web:
      place: web-app::signed-in::budget
---

# Share limited money inside one priority tier

## Trigger

There is not enough money for every goal of the same priority.

## Outcome

Ready to Assign reaches zero; lower tiers get nothing and the last tier is shared per the budget's setting.

## Decision points

### Sharing within a priority

How is the remaining money shared within the tier?

- Proportional shortfalls → each category gets the same fraction of what it still needs
- Equal completion percentage → the least-funded categories catch up toward one common completion percentage without taking money from others

## Edge cases

- A tier containing a goal whose monthly requirement is not positive is shared by proportional shortfalls whatever the setting.
